# Methodology

## Introduction

In this section, I will discuss my methodological approach to solving the problem statement which was how to tackle poor driving behavior behind the wheel of a vehicle, and what approaches I took during my research and development of my project to develop a lane-keeping system which aimed to reduce preventable car collisions on roads such as highways and urban cities. 

The core function behind lane assistive technology is to provide support to the driver by keeping them in their proper intended direction of travel [@SOC_Design]. The system uses a number of electronic components to collect data on the vehicle's lateral positional on the road surface. 

For the development of my project, I make use of the Unity Game Engine which is a cross-platform engine where the user can publish to a number of marketplaces, such as iOS, Google Playstore, PSN, or the Xbox Live marketplace. The ability to monetize an application is also possible but requires multiple licenses to do so. [@technologies]

## Software Development Life Cycle

Software development is described as the *'application of standard business practices to building software applications'*  [@SDLC]. The software development cycle follows several steps, 7 to be exact. Following these steps was key to the development of the project before you, as tasks were formed which could be broken down again into specifics. Once these tasks were discovered and taken note of it was time to identify and follow an SDLC model to follow. With a range of models that could be selected the author chose the model which best suited the criteria of their project.

## Waterfall Methodology

The chosen methodology for this project was the Waterfall approach, as it focuses on the project focuses on the progression of the previous step in order to progress and develop the next step to the project, and is known as a *'classic method of development'* [@SDLC]. One core benefit of using the waterfall method is that ensures a strong backbone for the development behind it and one drawback is that it reduces speed overall. It reduces overall development as the user may be stuck trying to develop a concept that just won't correctly work, which it needs to, in order to move forward. 

The diagram of the methodology used in this project was obtained by *'smartsheet.com'*

![Waterfall Methodology](03_figures/methodology/method.png)

## Unity Game Engine

Unity Game Engine was the version of control within this project. With having Unity multiple scenes could be created and gave the creator great control over all the possible parameters and acted as a great control since it was entirely editable, the engine makes great use of C# and C++ as programming languages to create scripts that make OOP (Object Orientated Programming) easier as everything within the engine supports the ability to attach scripts to it. 

![Unity User Interface](03_figures/methodology/Unity_GUI.png)

1. Unity makes use of a **hierarchy system** which contains all the user elements they are using within a specific scene. The window uses a parenting child system where the top element is considered the parent of the below element which would be the child. Every GameObject in the child position inherits the parents' properties. 

2. The **Scene** interface is where you can freely navigate the scene, it is the main interactive window you make sure of, the scene at default comes with a preloaded camera and light setup. From this view all GameObjects in the scene are visible. 

3. **Assests** like scene items which could be roads, cones, trucks, buildings are all available within the asset store. This made the creative process more exciting for the developer as the options were endless of what type of road networks they wished to create. All assets featured in the final project were obtained from free access through the use of the Unity assets store page. 

4. The **camera view** is a view that captures the display of what the user wants you to view as the player, in my case the camera was used as a 'Dash Cam' which was tasked to take a screenshot of what it was looking at every half second. I opted for a physical camera where I could adjust parameters such as FOV (field of view), aperture, and shutter rate. All screenshots were taken in a 500 x 500-pixel ratio which will be later examined later in the report. 

5. The **inspector panel** is what it sounds like, an inspection tool that allows you to view smaller components within the system. This tool was crucial to the development of the entire project as it allowed the author to see a graphical representation of everything within the scene. 

## Unity Scripts

A total of 7 C# scripts were created within Unity to develop this project. a detailed breakdown of all the scripts that were used entailed below:

### ArrowNPCMovement.cs

ArrowNPCMovement is a script that gets the navmesh agent component and waypoint manager and creates the objects. Once the objects were created the NPC (Non-Player Character) could head in the direction of the waypoints. Within this method, an update method is declared and this method is tasked to constantly calculate how far the NPC is to its waypoint and essentially apply the breaks as it gets closer. 

A method called *'HeadForNextWaypoint'* is also declared within this script, this method sets a target direction for the NPC to aim for and sets the direction is NPC needs to then go in. 

![ArrowNPCMovement Script](03_figures/methodology/ArrowNPCMovement.png)

### CarController.cs

### CarMove.cs

### Screenshotter.cs

Screenshotter.cs was heavily used in the development of the lane assist technology project. This file takes screenshots of every half second that passes in the game time, to do this a number of strings had to be created. Strings such as the file name, folder name, image number, file path, and a format had to be specified. The image width was also specified within this area, a screenshot below demonstrates how these were created which were then filled in using the Unity Engine Interface.

![Creating Screenshotter.cs](03_figures/methodology/Screenshotter_Script.png)



![Unity Screenshotter Utilization](03_figures/methodology/Screenshotter_Unity.png)

**void Start()** contains the key element of the screenshotting ability within the software. The start method is called when the scene is started before any of the Update() methods. A float is declared within the Start() method called *'start'* this contained the time interval for the first screenshot to start, which was every half second. The next float declared was the time for the next screenshot to be taken. This was again within a half-second and this was labeled the *'screenshotTimer'*. 

The method *'textureSaved'* is first introduced here, it is created as a string. The 3 declared variables were all then placed into a *'InvokeRepeating'* method which would invoke the variables every time Start() was run. 

![Start method](03_figures/methodology/Start_Screenshotter.png)


within the screenshotter script, a method called **'textureSaved()'** was created. The function of this method was to take the screenshots taken and save them to a folder destination within the hierarchy of the system. It took the screenshots that were taken and encodes them to PNG which is a type of format that is visible on most operating systems. It increments the images in a starting order of 0 - *n*. N being the final screenshot taken. Within this method, all images are encoded and saved as bytes which are added to the file path. 

![textureSaved method](03_figures/methodology/textureSaved.png)


### WaypointManager.cs

The waypoint manager script is a script directly interlinked with the navmesh path. This script takes in GameObjects which are considered to be waypoints, the script follows these waypoints(GameObjects) in a list order, for instance, 1-2-3-4 and so on. Once the script hits the last item in the list the script returns to the starting node. If there are no nodes added the script will return an error message to the user prompting them to add waypoints. This script is directly added to all car elements. 

![Waypoint Manager](03_figures/methodology/waypoints.png)


## Github 
The use of Github which is a free open source project developed by Linus Torvalds [@finley_2012], was heavily used as version control. This made tracking changes throughout the entire development of the project more manageable as it keeps track of every change made to any file.

Through the development of the project, there were two main Github repositories which were where any effective working code was pushed too which was visible to the authors' supervisor for future examinations. One repository contained the Python code behind the lane assistant technology which examined the road for lane lines. This repository was call *LaneAssist*. 

![LaneAssist Repository](03_figures/methodology/LaneAssist.png)



![Languages Breakdown](03_figures/methodology/Breakdown.png)

The other repository which was created contained all the Unity-based files. This contains every element used to create the entire scene that was used for demonstration. It also contains all C# scripts created which were attached to the GameObjects. The name of this repository was *LaneAssist_Unity*.

![LaneAssist_Unity Repository](03_figures/methodology/Unity.png)



![Unity Languages Breakdown](03_figures/methodology/Unity_Breakdown.png)

## Unity Nav Mesh Agent

The Unity navmesh agent is the agent which helps guide the vehicles in the scene around the test scenes. The process involves creating what is known as a *'navmesh'* with the aid of geometry level baking known as navmesh baking. When baking occurs in the scene all data related to terrains, paths and mesh render is collected from all the GameObjects within the scene. Any static GameObjects which do not move such as obstacles or walls are then identified and labeled accordingly in the navmesh agent. From this, the 'walkable' area is discovered and mapped out in a geometric way.   

![Path Creation](03_figures/methodology/NavMesh.jpg)



![Nav Mesh Agent Creation](03_figures/methodology/NavMesh_Agent.png)

When the area is baked within the see it will be outlined in a blue colour as soon as this path is now walkable for the navmesh agent. Factors such as radius, agents height, step height, and maximum slope should all be declared before baking. 

![Baking Settings](03_figures/methodology/Baking.png)


## Pycharm 

Pycharm Community Edition is a free open-sourced intelligent Python development IDE that includes a code assistant, packages, debugging, and most importantly version control. The version control tab was the tab that allowed the user to directly publish their repository. 

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

![Gradient Detection](03_figures/methodology/math.png)

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

## Summary

 