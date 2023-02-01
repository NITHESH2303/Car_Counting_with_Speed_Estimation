# Car_Counting_with_Speed_Estimation

# vehicle-counting-and-speed-estimation-yolo-sort-python

This project uses YOLOv3 for Vehicle detection and SORT(Simple Online and Realtime Tracker) for vehicle tracking

This project imlements the following tasks in the project: 

1. Vehicle counting
2. Lane segmentation
3. Lane change detection
4. Speed estimation
5. Dumps all these details into a CSV file

Note that there are 4 locations in the video and so the code(4 IFs), you can delete 3 and edit the first one according to your need.

# To run the project:

1. Download the code or simply run:
```
$ git clone 
``` 

2. To install required dependencies, run:
```
$ cd Car_Counting_with_Speed_Estimation

$ pip3 install -r requirements.txt
```

3. Download yolo weights file by:
```
$ bash download_weights
```  

4. Make sure you change the line of detection and lane segmentation according to your video and fine tune the threshold and confidence for YOLO model

5. Run 
```
$ Python3 main.py -input /path/to/video/file.avi -output /path/for/output/video/file.avi -yolo /path/to/YOLO/directory/
``` 




### Speed Detection:
This is an interesting project, mainly due to camera shaking(maybe due to wind or whaterver the reason may be!). This camera shake results into frame flickering. Which means we can not use traditional pixel distance travelled to Km/h mapping because as each frame flickers, the centroid of the bounding box also flickers arbitrarily. Hence I tried this new method: <b> SPEED BETWEEN TWO LINES</b>

#### Speed Between Two Lines (SBTL)
This method makes some assumptions which are as follows:
1. We know the speed limit of the road for which the video is recorded/streamed.
2. Atleast one vehicle is driving at the speed limit.

--> We draw two lines on the frame perpendicular to the vehicle moving directon, then we find the minimim time taken by any car to cross these two lines(This car will be moving at the speed limit). Once we find he minimum time required for a car to pass these two lines, we use simple speed=distance/time formula to calculate the speed for rest of the cars.[ I know this wouldn't be perfect, but surely much more precise than the pixel mapping method]



I will try to keep making commits to improve the speed detection of vehicles.
Any pull request for improvement is highly welcomed.



# References:


[YOLO](https://www.pyimagesearch.com/2018/11/12/yolo-object-detection-with-opencv/)

[SORT Algorithm](https://github.com/abewley/sort)

[Reference for combining YOLO and SORT](https://github.com/guillelopez/python-traffic-counter-with-yolo-and-sort)
