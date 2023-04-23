# NewSpaceEx1

![image](https://user-images.githubusercontent.com/92790326/233796654-01a98aee-d4ee-43cd-a5d7-5e18b740fdd5.png)

----

## By:
#### Sappir Bohbot - 316416429
#### Bar Goldenberg - 209894286
#### Hagai Hen - 313414872
----
## Task Detailed

This is task 1 in <course name>, 
the goal here is to create an algorithm for classifying stars, 
Given an image of stars and given a database of the positions of the stars - 
we would like to find a match between the stars in the image and those in 
the database. We can divide this task to 4 parts:
1. Formulate a simple but effective algorithm (when it is allowed to be based on existing algorithms - depending on the limitations).
2. To implement a library that receives an image of stars and converts them to a coordinate file (x,y,r,b the coordinate of each star will store x,y where r represents the radius, and b represents the brightness).
3. To implement a library which, given two images - calculates an optimal match between the images - by creating a list of coordinate pairs that point to the same star (in each of the images).
4. Summary of the work, in a large experiment on image libraries and presented the results of the developed algorithm.



---
## Technology.
We chose to write our prototype in [Python](https://www.python.org/), and since we had a lot of sketches, 
experimental code and liberties imported, we decided to use [Googles Colab](https://colab.research.google.com/). 
you can see our Colab page [here](https://github.com/HagaiHen/NewSpaceEx1/blob/main/New_Space_Ex1.ipynb) (just press on Open in Colab). 

![image](https://user-images.githubusercontent.com/92790326/233613447-aa216c1d-b675-47cf-be61-4f17da302622.png)

Libraries we used:
- [openCV](https://opencv.org/).
- [Numpy](https://numpy.org/).
- [matplotlib](https://matplotlib.org/). 
---
## Algorithm Explained.
### _Detection_
*Goal:* Given an image of stars, convert them to a coordinate file (x,y,r,b the coordinate of each star will store x,y where r represents the radius, and b represents the brightness).<br/>

*Input:* Image. <br/>
*Output:* List that contain all the locations of the stars (as {x,y,r,b}).

*_Algorithm:_*
1. Find contours in the image.
2. Set a list 'Centers' .
3. Loop through the contours, for each contour CNT:
   1. Calculate the bounding box of CNT (as {x,y,r,b}).
   2. Check if the bounding box of CNT is too close to any of the previous centers, if it too close - break.
   3. If CNT is not to close and the width and height of CNT are in scale, Calculate the center of the star and save it in 'Centers'.
4. return 'Centers'.
### _Matching_
*Goal:* Given two images - calculates an optimal match between the images - by creating a list of coordinate pairs that point to the same star (in each of the images).<br/>

*Input:* Two images. <br/>
*Output:* Optimal match between the images - by creating a list of coordinate pairs that point to the same star (in each of the images).


*_Algorithm:_*
1. Apply Detection Algorithm on img1 and img2 =result> rect1 and rect2.
2. Use [RANSAC Algorithm](https://en.wikipedia.org/wiki/Random_sample_consensus) to get the two pictures lines and top three points that representing this line.
3. In each rect, after phase II, there will be three points representing its RANSAC line - then can be interrupted as triangle.<br/>
    check the similarity of both triangles => which gives you the Ratio. 
4. Compute the transformation between img1 to img2, using the Ratio.
5. Draw the images after the transformation.

---
## Run Examples.

#### _Detection_

*ST_db2.png*
![image](https://user-images.githubusercontent.com/92790326/233796355-73c6a92f-7bd9-4db8-8eb5-7a8a8fb71aae.png)
<br/>
*IMG_3054.jpg*
![image](https://user-images.githubusercontent.com/92790326/233796363-346c628f-fa3b-4754-8c56-3ebc627eeec3.png) 
<br/>
*IMG_3053.jpg*
![image](https://user-images.githubusercontent.com/92790326/233796376-f882ace4-f6b7-48de-9109-e8ed7d97a9eb.png)
<br/>
#### _Matching_
![image](https://user-images.githubusercontent.com/92790326/233795849-7b44cf8c-accf-4ded-845d-5b0690a3c295.png)



For more examples you can look [here](https://github.com/HagaiHen/NewSpaceEx1/blob/main/New_Space_Ex1.ipynb).

 

fr1.jpg | | ST_db1.png
--- | --- | ---|
(1826, 3996, 6, 215) |=>| (545, 946, 6, 215) 
(1712, 3792, 10, 251) |=>| (511, 852, 10, 251)
(714, 3551, 8, 253) |=>| (105, 682, 8, 253)
(2871, 3189, 9, 253)  |=>| (1043, 676, 9, 253)
(1890, 3079, 2, 181) |=>| (635, 563, 2, 181)
(1754, 2785, 6, 242) |=>| (598, 429, 6, 242)
(648, 2752, 5, 212)| => |(132, 339, 5, 212)
(2495, 2661, 6, 238) |=> |(920, 427, 6, 238)
(2562, 2409, 8, 251) |=> |(965, 325, 8, 251)
(1961, 2390, 9, 254) |=>| (712, 276, 9, 254)
(2161, 2178, 8, 239) |=>| (811, 200, 8, 239)
(2815, 2160, 4, 200) |=>| (1089, 237, 4, 200)
(1461, 2111, 5, 250) |=>| (520, 124, 5, 250)
(1155, 2072, 1, 183) |=>| (393, 86, 1, 183)
(1670, 1982, 5, 253) |=>| (617, 84, 5, 253)
(1135, 1869, 7, 239) |=>| (398, 0, 7, 239)
(2715, 1759, 7, 224) |=>| (1075, 61, 7, 224)


For more examples you can look [here](https://github.com/HagaiHen/NewSpaceEx1/blob/main/New_Space_Ex1.ipynb).

 
