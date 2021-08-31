# Methodology

## Introduction

In this section, I will discuss my methodological approach to solving the problem statement which was how to tackle poor driving behavior behind the wheel of a vehicle, and what approaches I took during my research and development of my project to develop a lane-keeping system which aimed to reduce preventable car collisions on roads such as highways and urban cities. 

The core function behind lane assistive technology is to provide support to the driver by keeping them in their proper intended direction of travel [@SOC_Design]. The system uses a number of electronic components to collect data on the vehicle's lateral positional on the road surface. 

For the development of my project, I make use of the Unity Game Engine which is a cross-platform engine where the user can publish to a number of marketplaces, such as iOS, Google Playstore, PSN, or the Xbox Live marketplace. The ability to monetize an application is also possible but requires multiple licenses to do so. [@technologies]

## Unity Game Engine
Unity Game Engine was the version of control within this project. With having Unity multiple scenes could be created and gave the creator great control over all the possible parameters and acted as a great control since it was entirely editable, the engine makes great use of C# and C++ as programming languages to create scripts that make OOP (Object Orientated Programming) easier as everything within the engine supports the ability to attach scripts to it. 

![Unity User Interface](03_figures/methodology/Unity_GUI.png)

1. Unity makes use of a **hierarchy system** which contains all the user elements they are using within a specific scene. The window uses a parenting child system where the top element is considered the parent of the below element which would be the child. Every GameObject in the child position inherits the parents' properties. 

2. The **Scene** interface is where you can freely navigate the scene, it is the main interactive window you make sure of, the scene at default comes with a preloaded camera and light setup. From this view all GameObjects in the scene are visible. 

3. **Assests** like scene items which could be roads, cones, trucks, buildings are all available within the asset store. This made the creative process more exciting for the developer as the options were endless of what type of road networks they wished to create. All assets featured in the final project were obtained from free access through the use of the Unity assets store page. 

4. The **camera view** is a view that captures the display of what the user wants you to view as the player, in my case the camera was used as a 'Dash Cam' which was tasked to take a screenshot of what it was looking at every half second. I opted for a physical camera where I could adjust parameters such as FOV (field of view), aperture, and shutter rate. All screenshots were taken in a 500 x 500-pixel ratio which will be later examined later in the report. 

5. The **inspector panel** is what it sounds like, an inspection tool that allows you to view smaller components within the system. This tool was crucial to the development of the entire project as it allowed the author to see a graphical representation of everything within the scene. 

## Unity Scripts

A total of 7 C# scripts were created within Unity to develop this project. a detailed breakdown of all the scripts are entailed below:

### ArrowNPCMovement

### CarAI

### CarAI2

### CarController

### CarMove

### Screenshotter

Screenshotter.cs was heavily used in the development of the lane assist technology project. This file takes screenshots every half second that passes in the game time, to do this a number of strings had to be created. Strings such as the file name, folder name, image number, filepath, and a format had to be specified. The image width was also specified within this area, a screenshot below demonstrates how these were created which were then filled in using the Unity Engine Interface.

![Creating Screenshotter.cs](03_figures/methodology/Screenshotter_Script.png) <br>
![Unity Screenshotter Utilization](03_figures/methodology/Screenshotter_Unity.png)

**void Start()** contains they key element of te screenshotting ability within the software. Start is called when the scene is started before any of the Update() methods. A float is declared within the Start() method called *'start'* this contained the time interveal for the first screenshot to start, which was every half second. The next float declared was the time for the next screenshot to be taken. This was again within a half second and this was labelled the *'screenshotTimer'*. 

The method *'textureSaved'* is first introduced here, it is created as a string. The 3 declared variables were all then placed into a *'InvokeRepeating'* method which would invoke the variables everytime Start() was run. 

![Start()](03_figures/methodology/Start_Screenshooter.png)

### WaypointManager

## Github 
The use of Github which is a free open source project developed by Linus Torvalds [@finley_2012], was heavily used as version control. This made tracking changes throughout the entire development of the project more manageable as it keeps track of every change made to any file.

Through the development of the project, there were two main Github repositories which were where any effective working code was pushed too which was visible to the authors' supervisor for future examinations. One repository contained the Python code behind the lane assistant technology which examined the road for lane lines. This repository was call *LaneAssist*. 

![LaneAssist Repository](03_figures/methodology/LaneAssist.png) <br>
![Languages Breakdown](03_figures/methodology/Breakdown.png)

The other repository which was created contained all the Unity-based files. This contains every element used to create the entire scene that was used for demonstration. It also contains all C# scripts created which were attached to the GameObjects. The name of this repository was *LaneAssist_Unity*.

![LaneAssist_Unity Repository](03_figures/methodology/Unity.png) <br>
![Unity Languages Breakdown](03_figures/methodology/Unity_Breakdown.png)

## Unity Nav Mesh Agent

## Pycharm 

### main.py

blah blah blahhhhhhhhhhhhhhhhhhhhhhhhhhhhh


## Summary

 