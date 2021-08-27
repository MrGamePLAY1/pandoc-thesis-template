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
device. [@Sal18]S

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
### Conclusion of review 

To conclude my review of five different papers relating to my subject of lane assistive technologies
I feel I have a greater understanding of the subject as a whole. Reviewing the problems faced in
previous papers will help me identify future problems that will be faced in the coming weeks of
developing my project. The papers also provide potential means to avoid and solve these problems
that I may encounter when developing my project and will serve dearly.

The knowledge from reading past papers will prove of great importance in the development of the
project as the knowledge gained will make up for more development time and less time solving potential issues discovered in the past. This will ensure the final project will be a refined, polished
application in the closing weeks of the submission date for the project. 

