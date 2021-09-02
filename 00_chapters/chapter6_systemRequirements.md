# Testing of Python Computer Vision Sub-System

## Introduction

This chapter discusses the testing of the Python computer vision sub-system and evaluates how the developed project analysis' and processes images. 

## Testing Lane Detection

### Test 1: Image of Straight Road

Expected Output:

Lanes can be correctly identified within the given video made from the images passed to it. 

Output:

The algorithm can process the images it is given perfectly until it hits the end, where no lane is continued. Although there is a 10% +- deviation on where it thinks the lanes are. Overall I would say it has 95% accuracy

![100% accurate](03_figures/Testing_python/1.png)


![95% accurate](03_figures/Testing_python/2.png)


![90% accurate](03_figures/Testing_python/3.png)


### Test 2: Image of Curved Road

Expected Output:

Lanes can be correctly identified when going around a small bend.

Output:

The algorithm can process the images it is given perfectly until it hits the end, where no lane is continued. Again accuracy is within 80% range where it has slight deviations.

![100% accurate](03_figures/Testing_python/curve_1.png)


![95% accurate](03_figures/Testing_python/curve_2.png)


![70% accurate](03_figures/Testing_python/curve_3.png)


### Test 3: Image of Wall Road

Expected Output:

Lanes can be accurately be mapped before changing lanes and after.

Output:

The algorithm has a really difficult time in processing the lane accurately in this scene, the author believes this is because of the wall and how it can be potentially seen as a lane line with its straight edges. Accuracy is greatly reduced but returns when passed the wall


![80% accurate](03_figures/Testing_python/wall_1.png)


![70% accurate](03_figures/Testing_python/wall_2.png)


![0% accurate](03_figures/Testing_python/wall_3.png)


### Test 3: Image of Vertical Straight Road

Expected Output:

Lanes can be accurately be mapped while going vertical and forward

Output:

The algorithm has a really difficult time processing the lane accurately in this scene. On further inspection of the vehicle in motion of climbing the author noticed the vehicle on the test scene was not sitting perpendicular with the road surface. The author is unaware as to why this is but believes this could be the cause of the reduced accuracy.


![100% accurate on a tight bend](03_figures/Testing_python/busy_1.png)


![50% accurate](03_figures/Testing_python/busy_2.png)


![66% accurate](03_figures/Testing_python/busy_3.png)


## Conclusions

The author believes the software does effectively works while operating and navigating around slight bends and performed exceptionally well given such difficult circumstances when placed in an environment it is not intended to work within (Busy Town).

The author believes that Objectives 1 - 6 were successfully achieved in various degrees of success within the given time constraints. All the foundation work has been completed, and the general architecture allows testing (and comparison) of other lane assist components systems also allow for additional scenes with variations of road conditions and obstacles.

With future development the project could aid in a robust virtual testing system for lane assist systems, improving performance and evaluation of future lane assist systems.