# Literature Review
## Introduction 

The topic that I will be researching into is Lane Assistant Technologies and developments around that area of research, how people in the past have implemented methods of adding lane assist to their vehicles. This review will be based upon past papers about advancing technologies in this sector. The reason for writing this review is to get a better personal understanding about the current available understanding about the available technologies and how they were built and identifying current problems in the current technology that could be potentially phased out with future builds of the technology and how it could be improved upon. 

## Main Research Questions
- What is OpenCV and what can it do? 
- What are the current limitations faced? 
- Can this technology be fitted to every vehicle? 
- Will complex shadows hinder the technology?

### What is OpenCV and what can it do?

OpenCV is a library filled of programming functions that are aim at this idea of real-time computer vision, originally developed by Intel in June of the year 1999 and later to be supported by a robotics company Willow Garage and then Itseez, which was then acquired by Intel.

With the ability to solve small computer problems like “ray tracing” which is a method to accurately depict shadows and reflections from the real world and replicate them into a digital world, the uses for OpenCV became endless. The goal which was set by Intel back in 1999 was to create a software that contained critical optimized code which was portable the user which they hoped which would be free to use as the project was “Open Source” which meant anyone who wanted to add to the project could.

Within a few months of its launch, OpenCV gained more and more support within the programming community and programmers were adding to its usability adding more than 2500 optimized algorithms. With having more than 18 million downloads it has an incredible community backing it. With having such a big community behind it, OpenCV is perfect for novice C++ programmers looking to learn or C++ professionals the library has something to offer for all.

During the development of the proposed project of recreating lane assistant technology well-known algorithms such as “Haugh transformation” and “Canny Edge Detector” which are in the OpenCV library help with the core functionality of the software. They both serve to help find the edges of the road marking and help identify the road markings. [@Sal18]

### What are the current limitations faced?

Limitations are faced with any project, in many different layers of difficulty. A common problem
faced with papers that the author analyzed is related to obstructions such as car crashes how the software interprets
them. Any type of crash or incident faced can bring unique circumstances, different road marking
is a possibility, markings that are lined out using cones, or markers. Currently in the papers that
the author has analyzed the author cannot find a high success solution to get around this problem. 

A  part of a solution that can be used is making use of the “Canny Edge Detector” algorithm or to use machine deep learning. Canny edge detection algorithm combined with the “Hough Transformation” algorithm helps build a vision identifying
the markings on the road throughout the process.

![Canny Process](03_figures/litReview/Process.png)

Another problem identified in the papers that the author analyzed is weather conditions. With
weather conditions visibility of the road, markings can be difficult. This problem is identified in
the paper “Lane detection using canny edge detection and Hough transform on raspberry pi” In
this paper, the authors identify this being an issue that they faced, and discovered the following
findings, a researcher Q. Gao once proposed an algorithm using Gabor filtering and edge detection
for identifying lanes, this algorithm was suitable for fast lane detection in multilane situations. [@QGal17]

Another algorithm discussed in the same paper was discovered with being able to detect lanes and
vehicles simultaneously. V. Q. Nguyen proposed an approach using a mixture of a lane detection
algorithm and vehicle detection algorithm. This algorithm was useful in multi-lane situations. [@QGal17]

In all the papers examined, an ROI is a common thing discussed, this is a Region Of Interest (ROI)
which is identified. This is the area of the video that is being examined by the software to identify
road markings. A lane detection system proposed by C. B Wu determines the ROI in and then the
lane markings identified are then enhanced using higher pixel densities to combat different
environmental situations. [@CBw18]

### What is the future of lane assist technology?

After reviewing papers related to the development of a lane departure detection system it is evident
that the future of this technology is bright, with various algorithms supported by OpenCV and
developed by independent researchers. Many of the papers reviewed describe the process behind
real-time lane detection using many different forms of hardware some of which are using the
Raspberry Pi with aid of the Pi Camera. [@RJa18]

A paper written by Wael Farag and Zakaria Saleh talk about a LaneRTD (Lane Real-Time
Detection) software that they developed, this system was developed with the idea of being cost-effective for the end-user, it demonstrates the low computational cost of developing such software
but achieving an end goal also, which is to provide a low-cost effective solution for lane detection
device. [@Sal18]

It shows the potential future of the advancing technology as the paper talks about how the same
goal was achieved using a single CCD camera. The authors mention that approaches in other
projects making use of neural networks and deep learning algorithms. [@JLi16] promising a
bright future for the advancing technology.

### Can this technology be retrofitted to any vehicle?

In all the papers that were examined, they all show different ways to
achieving the goal of developing a lane departure system. In many different ways, this was
achieved, in the case of one paper a Raspberry Pi device coupled with a Pi Camera was used. This
was low budget but effective means of developing a lane departure system. [@RJa18]

Some papers talk about a more expensive option in developing a system, using IR sensors to help
detect road markings and making use of proximity sensors attached to the front and rear of a
vehicle, which can be retrofitted to a vehicle commonly known as parking sensors. [@RJa18]

None of the papers reviewed talk about one specific vehicle so, the answer to this question is yes,
the technology can be retrofitted to any vehicle as long as it has a clear view of the road the vehicle is directed towards. 

### Will complex shadows, snow or wet roads hinder detecting road markings?

As seen from the papers it is evident that a number of things can disrupt the functionality of the
software, from the gradient of the road to having no markings identifying the road, to harsh weather and
conditions such as dense fog. Many factors can disrupt the functionality of the software.
Specifically, in one of the papers written, it talks about how a complicated shadow confused the
software in thinking it was an obstacle in the road. This altered the perception of where the
software thought the road markings were, placing them in incorrect locations. What is suggested
in the paper to help reduce these complicated confusions are trying to add better-suited FIR parameters,
and *“trying different low pass polynomials like Butterworth, Chebychev, Ellipitcal, etc..”* [@Sal18]. 
The FIR filter is used to help reduce jitter on the indicators on the left and right lanes.

## Background Research

### Introduction

In recent years the number of cars on the road has been on a slow increase, due to more affordable ways of manufacturing them. With the increase of vehicles on the road car-related incidents are on the rise also. 
 
According to a study conducted by the RSA based in Ireland during the period of January - December 2020 there were a total of 137 fatal collisions which resulted in 148 on Irish roads. Which turns out to be a 6% increase of fatalities compared to provisional Garda data collected for the year of 2019 [@RSA_2021].
 
 
![Fatalities by year](03_figures/introduction/Road_Deaths.png)
 
The (NHTSA) National Highway Transportation Safety Administration discovered that roughly 94% - 96% of all car-related crashes are down to some type of human error. Meanwhile, other studies suggest that that figure is somewhere around the 90% range. [@lc_2020]

Through a deeper investigation and analysis into this claim, it is found that a high percentage of crashes could of be adverted, as the majority of incidents reported were down to specific driver behavior in a given situation. Most of the accidents that were recorded would fall under a number of categories such as:

* Aggressive / Dangerous Driving
* Distracted Driving
* Drug / Drunk Driving
* Speeding
* Fatigued Driving

### Aggressive / Dangerous Driving

In today's version of the world with cities expanding and areas becoming more and more populated, everyone is in a rush trying to get to work or one place to another and the slightest inconvenience to someone's day could enrage them which could lead to dangerous or aggressive driving from that particular user. 

### Speeding

According to a study conducted by the (NHTSA) National Highway Transportation Safety Administration, more than 9,000 worldwide people are killed each year due to excessive speeding. [@lc_2020]

As a road user myself I have foreseen that speeding is a common practice undertaken by other road users. It is difficult not to 'normalise' speeding since it appears to be a victimless crime until it goes wrong, and when it goes wrong it could lead to a catastrophic result. It endangers everyone in the vicinity as it increases the braking distance for the vehicle but simultaneously decreases the distance from any approaching obstacles, you are effectively burning the candle at both ends. [@lc_2020] 

### Distracted Driving

With the ability to have everything on your phone in this modern era such as emails, video calls, and the ability to watch videos, you can see how much of a temptation it is for a driver to operate a vehicle and mobile device at the same time. It is common to see a user operate a mobile device while driving a vehicle and can have very serious consequences if caught doing so, but users still take the risk. 

### Drug / Drunk Driving

It is estimated in America that under the influence related crashes cost American taxpayers $44 billion each year. [@lc_2020] And that during a 15-year study conducted by S. News & World discovered that 37% of all fatal car-related crashes included at least one occupated that was intoxicated [@lc_2020].   

### Fatigued Driving

A survey done by (NSF) Nation Sleep Foundation discovered that 41% of all drivers interviewed admitted to falling asleep at the wheel at least once in their life and that 10% reported it occurred within the past year. [@lc_2020] Even if the driver didn't fall asleep driving fatigued is like driving drunk, your reaction times are slowed and your vision is reduced.  

## Lane Keeping Assist Systems
 
 From the evidence pointed out above a system needed to be implemented to reduce the number of car-related incidents globally. This was known as (LKAS) Lane Keeping Assist System and was brought to the market in the year 2001 [@continental]. The aim behind the technology is to prevent, easily preventable car-related incidents, such as driver fatigue, drug driving, distracted driving, and so on. The first car seen with an (LKAS) system on the market was seen with Nissan Motors as they revealed the first version of the technology in the most luxurious vehicle they offered at the time, the Nissan Cima.

The main function behind the LKAS system is to ensure a user of a vehicle can safely travel in between lanes and prevent accidental lane departure from user error or fatigue, it does this by slightly intervening steering if the technology notices the car is drifting horizontally. [@continental]

Since the introduction of this technology, it is estimated to reduce car-related fatalities by 12%. [@ncap_2011] The systems vary on how they work from car manufacturers, but the concept still remains the same. A combination of a camera and the infrared beam is located just behind where the front rearview mirror is located. This unit together can read any road markings and detect the distance of any car in front. With the ability to detect the road markings on the road as it sees it the camera can
distinguish behind solid white lines and broken lines. If a solid white line is detected an audible
sound will play, letting the operator of the vehicle know that they are passing this line, or a
message will be displayed on their Heads-Up Display (HUD). [@continental]

The current issue with LKAS systems is the fact that they have strict parameters which don't suit all drivers with their habits. Some drivers prefer driving closer to the centerline, some like driving directly in the middle of their given lane, and some drivers prefer to drive on the outside of the lane. This can throw off any calculated percentages for the users' position on the road and may alter the driver to false indications of wrong lane positioning, which could cause a premature intervention by software to adjust the users' position on the road to what it thinks would be more suitable, which causes a real danger on the road. A better approach for this software is for the software to learning the driving patterns of the intended user and save that to a given profile the user can select before taking off on journeys, this way the software would identify false indications by prompting questions to the user when they drive in a 'dangerous' determined by the system. 

Another issue known by the current LKAS systems is the fact that if there are poorly marked roads or for example construction zones on the road, Infiniti a car manufacturing company and user of LKAS systems stated that *"if there are no lane markers, or the system is not able to recognise the lines, the system will not function effectively"*. [@ncap_2011]

## Conclusion 

To conclude this review of five different papers relating to the subject of lane assistive technologies
it was possible to develop a greater understanding of the subject as a whole. Reviewing the problems faced in
previous papers will helped identify future challenges to be faced. The papers also provide potential means to avoid and solve these problems
that they may encounter when developing my project and will serve dearly.

The knowledge from reading past papers will prove of great importance in the development of the
project as the knowledge gained will make up for more development time and less time solving potential issues discovered in the past. This will ensure the final project will be a refined, polished
application in the closing weeks of the submission date for the project. 

