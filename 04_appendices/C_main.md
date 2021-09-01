
# WebApplication.php

Code listing for `/src/WebApplication.php`. This class is the decision-making logic for the application to decide how to respond to the HTTP Request message received by the web application.

```python
import glob
import os
import cv2 as cv
import matplotlib.pyplot as plt
import numpy as np


def read_images():
    global name
    path = 'images/Busy Town/'

    for name in os.listdir(path):
        if name.endswith(".png") or name.endswith(".jpg"):
            # name.__str__()
            # print(name)

            # Read the image
            image = 'images/Busy Town/' + name  # cv.imread("images/Straight Vertical/" + name)

            array_of_image_urls = [image]
            # print(array_of_image_urls)
            image = cv.imread(image)
            cv.imshow("Raw Stock Image", image)
            break

            # Destroy window when pressing Q
            cv.waitKey(0)  # & 0xFF == ord('q')
            cv.destroyAllWindows()
        else:
            continue
    return image


def create_video():
    img_array = []
    for filename in glob.glob('images/Curve Road/*.png'):
        img = cv.imread(filename)
        height = img.shape[0]
        width = img.shape[1]

        size = (width, height)
        # print(size)
        img_array.append(img)

    video_output = cv.VideoWriter('video.mp4', cv.VideoWriter_fourcc('M', 'J', 'P', 'G'), 5, size)

    for i in range(len(img_array)):
        video_output.write(img_array[i])
    video_output.release()


create_video()

image = read_images()


# plt.imshow(image)
# plt.title("Stock Image")
# plt.show()

# Press 'Q' to close window
def quit(subject):
    if subject.key == 'q':
        plt.close()


def image_grey(original_img):
    # Image conversion to black and white
    original_img = cv.cvtColor(original_img, cv.COLOR_BGR2GRAY)

    # Show the image
    # plt.title("Image Grey Scaled")
    # plt.imshow(original_img, cmap='gray')
    # plt.show()
    return original_img


# Function to Blur the image
def image_blur(grey_image):
    # Bluring the image
    Img_blur = cv.GaussianBlur(grey_image, (5, 5), 0)

    # plt.title("Image Blurred")
    # plt.imshow(Img_blur, cmap='gray')
    # plt.show()
    return Img_blur


# The blurred Image returned (calls function)
# blur = image_blur(grey_Image)


# Canny Edge Detection - passing the blurred grey image
def image_canny(blur_img):
    img_canny = cv.Canny(blur_img, 100, 250)
    # plt.title("Canny Image")
    # plt.imshow(img_canny, cmap='gray')
    # plt.show()
    return img_canny


# Canny Image (calls function)
# canny = image_canny(blur)
# The grey Image returned (calls function)
grey_Image = image_grey(image)


# Function looks at just the white road lines.
# Using HSV Colourspace (Hue, Saturation, Value)
def identify_lines(img):
    original_img = cv.cvtColor(image, cv.COLOR_BGR2HSV)

    # Identifying the white line using HSV placing into np.array
    upper_white = np.array([255, 7, 230], dtype=np.uint8)
    lower_white = np.array([0, 0, 0], dtype=np.uint8)

    # Masking the white
    white_mask = cv.inRange(original_img, lower_white, upper_white)

    # A threshold to target only white colours in the image
    masked_image = cv.bitwise_and(img, white_mask)

    # plt.imshow(masked_image)
    # plt.title('Masked white image')
    # plt.show()

    return masked_image


lane_lines = identify_lines(grey_Image)


# Declaring a region of interest within an image
def region_of_interest(img):
    # Getting height and width of the image we want to use
    img_height = img.shape[0]
    img_width = img.shape[1]
    print("Image Height", img_height)
    print("Image Width", img_width, '\n')

    roi_triangle = np.array([
        [(0, 478), (440, 216), (490, 216), (img_width, img_height)]
    ])

    # Creating a mask for the image
    img_mask = np.zeros_like(img)

    # Combining the mask
    img_mask = cv.fillPoly(img_mask, roi_triangle, 255)
    img_mask = cv.bitwise_and(img, img_mask)

    # Displaying
    # plt.imshow(img_mask)
    # plt.title("Masked ROI Image")
    # plt.show()

    return img_mask


roi = region_of_interest(lane_lines)


def all_preprocessed_images():
    path = "images/Curve Road/*"
    imgNum = 0
    for name in glob.glob(path):
        img = cv.imread(name)
        # print(name)
        if name.endswith(".png"):
            img_canny = cv.Canny(img, 100, 250)
            cv.imwrite('images/CANNY/' + str(imgNum) + '.png', img_canny)

            img_crop = region_of_interest(img_canny)
            cv.imwrite('images/ROI/' + str(imgNum) + '.png', img_crop)

            original_img = cv.cvtColor(img, cv.COLOR_BGR2GRAY)
            cv.imwrite('images/ORIGINAL/' + str(imgNum) + '.png', original_img)
            imgNum += 1
    return


all_preprocessed_images()


def hough_algorithm():
    # This is an array
    hough_transform_output = cv.HoughLinesP(roi, rho=2, theta=3.642 / 180, threshold=75, minLineLength=40, maxLineGap=1)

    # Displaying
    # print(type(lane_lines_array))
    # print(lane_lines_array)

    return hough_transform_output


lane_lines_array = hough_algorithm()


def average_function(value):
    start = 0
    for i in value:
        start = start + i

    average = start / len(value)

    return average


def display(masked_image, output):
    black_img = np.zeros_like(masked_image, 'uint8')

    # Simple if statement to discover lines
    if output is not None:
        for single_line in output:
            variablex1, variabley1, variablex2, variabley2 = single_line

            print("x1 ", variablex1)
            print("y1 ", variabley1)
            print("x2 ", variablex2)
            print("y2 ", variabley2)

            # Drawing the line onto the black image
            cv.line(black_img, (variablex1, variabley1), (variablex2, variabley2), (148, 0, 211), 11)
    else:
        print("No lines detected")

    return black_img


def lane_line_average(declared_roi, hough_transform_lines):
    left_lane_arr = []
    right_lane_arr = []

    for line in hough_transform_lines:
        # Array from hough transformation
        print(line)
        x1_variable, y1_variable, x2_variable, y2_variable = line.reshape(4)

        # print("x1: ", x1)
        # print("y1: ", y1)
        # print("x2: ", x2)
        # print("y2: ", y2)

        x1_array_numpy = np.array(x1_variable)
        y1_array_numpy = np.array(y1_variable)
        x2_array_numpy = np.array(x2_variable)
        y2_array_numpy = np.array(y2_variable)

        # Type = (numpy.ndarray)
        # print(type(x1_array))

        print("x1_array_numpy", x1_array_numpy)
        print("y1_array_numpy", y1_array_numpy)
        print("x2_array_numpy", x2_array_numpy)
        print("y2_array_numpy", y2_array_numpy, "\n")

        # Polynomial fit (finds the least square polynominal fit)
        # (best fitting curve to a given set of points)
        # using x1, x2, y1, y2
        polyfit_value = np.polyfit((x1_variable, x2_variable), (y1_variable, y2_variable), 1)
        print("polyfit_value = ", polyfit_value)

        slope_of_line_seg = polyfit_value[0]
        y_intercept = polyfit_value[1]
        print("polyfit_value[0] (slope_of_line_seg) = ", polyfit_value[0])
        print("polyfit_value[1] (y_intercept) = ", polyfit_value[1], '\n')

        if slope_of_line_seg < 0:
            # If the slope is < 0 add to left_lines array
            left_lane_arr.append((slope_of_line_seg, y_intercept))
        else:
            # else add to right_lines array
            right_lane_arr.append((slope_of_line_seg, y_intercept))

    # We expect left line to start with NEGATIVE slope
    print("Left Line Values [NEGATIVE SLOPE] = ", left_lane_arr)
    print("Right Line Values [POSITIVE SLOPE] = ", right_lane_arr, '\n')

    # Averaging the values we got from left_lane, right_lane tuple arrays
    # Axis=0 computes the mean value over flattened array, along with rows
    left_lane_average = np.mean(left_lane_arr, axis=0)
    right_lane_average = np.mean(right_lane_arr, axis=0)
    print("Left lane average number: ", left_lane_average)
    print("Right lane average number: ", right_lane_average, "\n")

    # Adding the points to all masked image
    right_lane_line = calc_lane_point(roi, right_lane_average)
    left_lane_line = calc_lane_point(roi, left_lane_average)

    return [left_lane_line, right_lane_line]


# This function averages the lines taken in from the hough_algorithm() function
# It finds the average slope and y intercepts per line segment
# Displaying one slide line
def calc_lane_point(masked_image, lane_point_average):
    slope_of_line, y_intercept = lane_point_average

    # This is the image height of the given image we pass
    y1_val = 540
    print("This is the y1_val", y1_val)

    # This is how long we want the lines to be in our image
    y2_val = 405
    print("this is the y2_val", y2_val)

    x1_val = int((y1_val - y_intercept) / slope_of_line)
    print("This is x1_val", x1_val)

    x2_val = int((y2_val - y_intercept) / slope_of_line)
    print("This is x2_val", x2_val)

    return [x1_val, y1_val, x2_val, y2_val]


main_video = cv.VideoCapture("video.mp4")
while main_video.isOpened():

    #Read the current frame of the video
    ret, current_frame = main_video.read()

    cn = image_canny(current_frame)
    cp_img = region_of_interest(cn)
    h_lines = cv.HoughLinesP(cp_img, rho=1, theta=3.642 / 180, threshold=120, minLineLength=15,
                           maxLineGap=50)
    a_lines = lane_line_average(current_frame, h_lines)
    line_image = display(current_frame, a_lines)
    final = cv.addWeighted(current_frame, 0.8, line_image, 1, 2)

    cv.imshow("result", final)
    cv.waitKey(1000)

'''## THE CORE OF THE WORK ##'''
#img_copy = cv.imread('images/Curve Road/image0006.png')
img_copy = np.copy(image)

# Step 1: Turn the image grey
grey = image_grey(img_copy)

# Step 2: Add the blur
blur_grey_img = image_blur(grey)

# Step 3: Canny Edge
edge_detection = image_canny(blur_grey_img)

# Step 4: Isolate our area of interest
region = region_of_interest(edge_detection)

# plt.imshow(region)
# plt.title("ROI")
# plt.show()

# Step 5: Hough Transformation
output = cv.HoughLinesP(region, rho=2, theta=3.642/180, threshold=75, minLineLength=35, maxLineGap=1)

# Step 6: Average the lines found
avg = lane_line_average(img_copy, output)

print("Average Lines", avg)

# Step 6: Add blue lines to mask
blue_lines = display(img_copy, avg)

# Step 7: Add the wights to the image
add_weights = cv.addWeighted(img_copy, 0.8, blue_lines, 1, 1)

# Step 8: Display
plt.imshow(add_weights)
plt.title("Please work")
plt.show()

read_images()

```

    