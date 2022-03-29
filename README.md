# Internship-Project-At-DeepCell-Bio
### A brief detailing of the relevant work I did at DeepCell Bio.

<a href="url"><img src="https://media-exp1.licdn.com/dms/image/C5622AQHCoo6f6pEbiQ/feedshare-shrink_2048_1536/0/1646788805617?e=1651104000&v=beta&t=nWuWp3gsjSsoi1wMX10p5sdSbjlh1sEI4Z-J_0juoiM" height="600"></a>

(Image source: https://www.linkedin.com/posts/euanashley_after-5-years-of-development-starting-in-activity-6907132880326152192-3Asc?utm_source=linkedin_share&utm_medium=member_desktop_web) 
 
Recently, biotech startup DeepCell Bio put out a paper(linked at the bottom of this README), detailing the process of creating and the specifications of their COSMOS project. COSMOS classifies and sorts cells by their morphology using non-intrusive high-speed imaging and image analysis, based on deep machine learning.  

Since these live cells are moving through a microscopic tube at high speeds, the time between the point at which an image of the cell is captured and the point at the cell needs to be sorted is extremely small. Due to the irregular shape of the cells, traditional image processing frameworks fall short of expectations.  Thus, I was assigned the responsibility of porting an in-house Python blob detection library to C to optimize for runtime. 

![Screenshot (240)](https://user-images.githubusercontent.com/41028399/160461659-c9020860-6e64-43a7-a059-309e5e20dd8a.png)
(Image source: https://www.linkedin.com/pulse/marching-towards-new-omic-deepcell-mahyar-salek/)

In short, the blob finding algorithm removes background noise, binarizes the resulting image into black and white pixels, and stores the binarized output in a two dimensional array. It then iterates through the array to find blobs consisting of black pixels that neighbor each other cardinally or diagonally, recording the size and center of the blobs as new pixels are added to them. Finally, it merges blobs in close proximity together once the array has been fully iterated through.

In order to further optimize for time, I integrated OpenMP into the port to utilize parallel processing to achieve maximum efficiency. By distributing the loop's iterative calculations between multiple threads, runtime improved dramatically. 

Due to these improvements, the average runtime for the blob analysis algorithm dropped to less than half a millisecond on average, which was more than fast enough to meet the demands of COSMOS's first iteration.

The aforementioned paper going into further detail on the functionality, application, and making of COSMOS can be found at the link below.
https://www.biorxiv.org/content/10.1101/2022.02.28.482368v1.full 

Many thanks to the DeepCell team for allowing me to be a part of this project.
