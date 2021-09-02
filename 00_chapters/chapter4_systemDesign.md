# System Design and Implementation

## Introduction

This chapter discusses the components within the final system.

(a) Unity Test Scenes - In this there are developed 'scenes' in a Unity created environment featuring some easy navigatable areas such as straight roads, to slightly more complex test scenes which are a slight bend in the path, to the most difficult paths to navigate which include a busy town setting with multiple obstacles in the way. This part of the project demonstrates the normal operations of a vehicle using AI (NavMesh Agents) to navigate to waypoints placed in an orderly sequence. The advancing difficulty in test scenes will display any weaknesses in the system which can be improved upon on future builds.

![Unity Test Scenes](03_figures/System_Design/scenes.png) 

(b) Python Lane Assist Vision Processing - This component of the system examines all gathered images from the Unity component and processes each image and examines them in search for lane lines to then identify and mark. 

## Unity Nav Mesh Agent

The Unity navmesh agent is the agent which helps guide the vehicles in the scene around the test scenes. The process involves creating what is known as a *'navmesh'* with the aid of geometry level baking known as navmesh baking. When baking occurs in the scene all data related to terrains, paths, and mesh render is collected from all the GameObjects within the scene. Any static GameObjects which do not move such as obstacles or walls are then identified and labeled accordingly in the navmesh agent. From this, the 'walkable' area is discovered and mapped out in a geometric way.   

![Path Creation](03_figures/methodology/NavMesh.jpg)



![Nav Mesh Agent Creation](03_figures/methodology/NavMesh_Agent.png)

When the area is baked within the see it will be outlined in a blue colour as soon as this path is now walkable for the navmesh agent. Factors such as radius, agents height, step height, and maximum slope should all be declared before baking. 

![Baking Settings](03_figures/methodology/Baking.png) 

## Unity Cars

The cars used in the project were obtained from the *'Standard assets'* package offered to users of the Unity Game Engine software. It is free to download assets recommended by Unity for developers to develop within their projects. The package contains one vehicle 3D model which the author used in the development of the project. It is designed to replicate an actual car seen on roads. 

![Car Model](03_figures/System_Design/car.png) 


## Unity Engine

Within a Unity Scene, there is a number of test tracks. These test tracks are tracks is where the Unity Navmesh will navigate the appropriate track and gather images as it travels the entire length of the planned route. Once it completes and hits the last node it will return to its first waypoint, completing one loop, this loop should contain all the images needed. 

Once all the test tracks are completed all the images should be gathered which are then brought over to PyCharm and distributed into the correct folder relating it back to the appropriate folder.

A total of 7 C# scripts were created within Unity to develop this project. a detailed breakdown of the core scripts that were used is entailed below:


### ArrowNPCMovement.cs

ArrowNPCMovement is a script that gets the navmesh agent component and waypoint manager and creates the objects. Once the objects were created the NPC (Non-Player Character) could head in the direction of the waypoints. Within this method, an update method is declared and this method is tasked to constantly calculate how far the NPC is to its waypoint and essentially apply the breaks as it gets closer. 

A method called *'HeadForNextWaypoint'* is also declared within this script, this method sets a target direction for the NPC to aim for and sets the direction is NPC needs to then go in. 

![ArrowNPCMovement Script](03_figures/methodology/ArrowNPCMovement.png)

### Screenshotter.cs

Screenshotter.cs was heavily used in the development of the lane assist technology project. This file takes screenshots of every half second that passes in the game time, to do this a number of strings had to be created. Strings such as the file name, folder name, image number, file path, and format had to be specified. The image width was also specified within this area, a screenshot below demonstrates how these were created which were then filled in using the Unity Engine Interface.

![Creating Screenshotter.cs](03_figures/methodology/Screenshotter_Script.png)



![Unity Screenshotter Utilization](03_figures/methodology/Screenshotter_Unity.png)

**void Start()** contains the key elements of the screenshotting ability within the software. The start method is called when the scene is started before any of the Update() methods. A float is declared within the Start() method called *'start'* this contained the time interval for the first screenshot to start, which was every half second. The next float declared was the time for the next screenshot to be taken. This was again within a half-second and this was labeled the *'screenshotTimer'*. 

The method *'textureSaved'* is first introduced here, it is created as a string. The 3 declared variables were all then placed into a *'InvokeRepeating'* method which would invoke the variables every time Start() was run. 

![Start method](03_figures/methodology/Start_Screenshotter.png)


within the screenshotter script, a method called **'textureSaved()'** was created. The function of this method was to take the screenshots taken and save them to a folder destination within the hierarchy of the system. It took the screenshots that were taken and encodes them to PNG which is a type of format that is visible on most operating systems. It increments the images in a starting order of 0 - *n*. N being the final screenshot taken. Within this method, all images are encoded and saved as bytes which are added to the file path. 

![textureSaved method](03_figures/methodology/textureSaved.png)


### WaypointManager.cs

The waypoint manager script is a script directly interlinked with the navmesh path. This script takes in GameObjects which are considered to be waypoints, the script follows these waypoints(GameObjects) in list order, for instance, 1-2-3-4 and so on. Once the script hits the last item in the list the script returns to the starting node. If there are no nodes added the script will return an error message to the user prompting them to add waypoints. This script is directly added to all car elements. 

![Waypoint Manager](03_figures/methodology/waypoints.png)


## Python System

The reason behind the use of Python in this project is because Python is used in AI and machine learning, Python is among the best and favourite languages when developing ML and AI projects. Also, a quick Google search will demonstrate the sheer amount of packages and libraries available to an end-user for developing such projects.

### main.py

This Python file is the core of calculations and determination for identifying lane lines and then drawing them onto a live video. The file features a number of core methods which will be discussed below.

**def read_images()** 


This method is responsible for reading in all images which are contained within a folder that was brought over from Unity. Within the project hierarchy, the images that were used in the final pipeline of the project were separated into folders labeled 'Busy Town', 'Straight Road', 'Straight Vertical' and 'Wall Road'. These names of the folder represent what test section within Unity the screenshots came from. For example 'Straight Road' was a section of road where the road went perfectly straight and featured no obstacles which would stress test the system.  

**def create_video()** 


This method creates the final video outputted for the lane detection algorithm to then examine. It adds all images discovered within a path identified with the codec of PNG and adds them in ascending order with a framerate of 5 to a video format of mp4. The final output is 'video.mp4' which has a framerate of 5fps. 

![Video Creation](03_figures/methodology/vidOutput.png)

**def image_grey(original_img)** 


This method aims to be more computational resourceful in the processing of images, since RGB images are bigger in size they would be more costly in performance when processing them, this is why within this method all images are converted to grey. This is done by using the OpenCV library which was heavily used within this part of the project. This method requires the image or images that the user would like to be processed. 

**def image_canny(images)** 


The image canny method requires a set or single image and uses a famous algorithm called Canny edge detection to discover a set of harsh edges within a given image. The algorithm provided within the OpenCV Library requires parameters such as two individual threshold values a minimum and a maximum and set or single images. The output of what canny edge algorithm and the mathematical formula behind the algorithm can be seen below.

Note: The mathematical formula was obtained from the official documentation page for OpenCV which is located at, https://docs.opencv.org/3.4/da/d22/tutorial_py_canny.html

![Gradient Formula](03_figures/methodology/math.png)

![Sample Output From Project](03_figures/methodology/canny.png)

**def identify_lines(images)** 


Identifying lines within a given image is one of the core functional components of the project. Preprocessing steps such as declaring an ROI should be done by this step and the image should be already pre-processed by canny edge detection to focus the search to a specific area. In this method HSV (Hue, Saturation, Values) values are targetted, Since the author knew that lane lines in their scene were a specific colour they targetted them with very specific HSV values with an upper and lower index of the same colour. 

**def region_of_interest(images)** 


A region of interest or ROI is a very important concept behind identifying lane lines, this concept focuses on declaring a region the author planned to examine and narrows the focus on a specific site. Within this function, 4 points would map an area in space in a given image that would be masked as visible while areas outside the mask would be discarded. This function would return the ROI with the image canny as the canny image is recommended to be passed by this stage.

![Sample ROI From Project](03_figures/methodology/ROI.png)

**def hough_algorithm()** 


Hough transformation algorithm is a well-known algorithm to detect shape within an image, it is then displayed in a mathematical form. Within the author's hough_algorithm function the author makes heavy use of the probabilistic hough transform provided by the OpenCV library. The reason behind this is simply because it is a refined version of hough transformation as it takes in all points into consideration in a given set of images. The result is a cleaner less noisy output. 

parameters require to be fulfilled to effectively make use of the hough lines algorithm. parameters such as a given set of lines detected within the ROI are passed, with 'rho' values which represent the resolution declared in pixel values. Another value passed is known as 'theta', which is the resolution value that is declared in radians. Finally, the final values which were 'maxLineGap' and 'minLineGap' which are related to the dimension of the road were input. The output from the hough transformation was in the form of an array which was later changed to a NumPy array.

![Declaring HoughLinesP](03_figures/methodology/houghLinesP.png)

## Intensions

The original plan for the project was to create a system where the ability for communication between the two components would be used, for example within the Python system there would be a socket server or web server listening out for any incoming data which would have been sent from the Unity project. The incoming data would be the screenshots taken within Unity which would have been stored in a folder, but complications with the Unity Screenshotter prevented this deployment. 

## Summary

This chapter talks about the Unity car asset which came from the standard assets pack recommended by Unity, it also goes talks about the Unity Engine and tools within Unity UI scene. The author also discusses how functions from the C# and Python scripts work and talks about the core methods that were implemented.  