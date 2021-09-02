# Testing of Unity virtual driving environments sub-system

## Introduction

In this chapter, the author discusses the results discovered in the final output from the project. The author discusses the current state of the project and evaluates the project on areas that could be improved upon, from user testing. With each test scene, the algorithm will be forced to attempt and the performance is documented.

## Testing AI car on each track

### Test 1: Straight Road

Expected behaviour: 

The car stays within its given lane line, keeping a safe distance between the two edges.

Result: 

The car navigates through the course perfectly keeping a perfect distance between the lane perimeters.

![Curve Road](03_figures/Results/STOP.png)

### Test 2: Curved Road

Expected behaviour: 

The car stays within its given lane line and safely corrects itself when approaching the slight curve in the road.

![Curve Road](03_figures/Results/bend.png)

Result: 

The car navigates through the course but sometimes gets too close to the left side of the barrier. for an unknown reason and it is labeled 'not navigatable by the author. The author believes the AI system is using the shortest distance possible from it and the waypoint as it navigates towards it. 

### Test 3: Wall Road

Expected behaviour: 

The car stays within its given lane line and safely avoids the clear stone walls placed in front of it to reach the checkpoint behind it. 

Result: 

The car navigates through the course but comes close to each wall as it passes by. But overall it safely passes the obstacles. 

![Wall Road](03_figures/Results/wall.png)

### Test 4: Vertical Straight Road

Expected behaviour: 

The car stays within its given lane line and climbs the vertical distance without slowing or falling backward as gravity affects it. 

Result: 

On initial testing, the car could not travel vertically due to its mass and weight combined with the set power for forwarding motion it was given. But upon tweaking settings within the car's properties it could safely ascend and descend at the same speed reaching its waypoints.

![Vertical Straight Road](03_figures/Results/45.png)

### Test 5: Busy Town

Expected behaviour: 

The car stays within its given lane line, and can safely avoid the clearly placed objects within the scene, and safely overtake cars while keeping good lane discipline. 

Result: 

On initial testing, the car crash almost immediately as it approached corners way too quickly and slowly applied the breaks which would catapult the car into oncoming traffic. Adding more waypoints near the corners, this reduced the speed of the car approaching corners and tightened the cornering circle required to take hard corners, which improved the lane discipline.

![Busy Town](03_figures/Results/navPath.png)


## Sub-system (Screenshotter)

The screenshotter sub-system worked as intended within the system. It took a screenshot every half second but could not process and individually place every screenshot from all running tests into the same folder. Having it try to do so slowed the author's PC down to 5-7 fps when running the scene as it was extremely resource intensive to have each of the five test scenes take a single screenshot which are 960 x 540 pixels tall every half second. A single run of the environment in terms of screenshots for a curved road scene is demonstrated below.

![Screenshots in Unity](03_figures/Results/screenshot.png)


## Summary

* The car can safely navigate all test scenes appropriately.


* The camera stills are taken every 0.5 seconds of the car taking off from its original standing position, which accurately functions like a dash camera in real life.


* NavMesh Agent is fully operational and avoids static objects.


* Not yet possible to test the connection between lane assist sub-system and lane assist the controlled car in a time frame of this project, but all the foundation work has been completed.



