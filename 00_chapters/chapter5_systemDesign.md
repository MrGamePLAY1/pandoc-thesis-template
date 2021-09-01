# System Design

## Introduction
This chapter talks about how the system works using charts designed to demonstrate the process of how screenshots from built test scenes in Unity are read and used within the main.py program. 

![Low-level Unity Pipeline to PyCharm](03_figures/System_Design/unityPipeline.png)


Within a Unity Scene, there is a number of test tracks. These test tracks are tracks is where the Unity Navmesh will navigate the appropriate track and gather images as it travels the entire length of the planned route. Once it completes and hits the last node it will return to its first waypoint, completing one loop, this loop should contain all the images needed. 

Once all the test tracks are completed all the images should be gathered which are then brought over to PyCharm and distributed into the correct folder relating it back to the appropriate folder.

![Low-level Processing Images](03_figures/System_Design/PyCharm.png)

This is a representation of the entire pipeline and how all components connect with each other. 


![Entire Pipeline](03_figures/System_Design/entirePipeline.png)

 

## Summary