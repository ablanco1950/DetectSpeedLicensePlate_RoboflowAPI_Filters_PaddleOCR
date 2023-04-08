# DetectSpeedLicensePlate_RoboflowAPI_Filters_PaddleOCR
This work is an extension of the project https://github.com/ablanco1950/LicensePlate_RoboflowAPI_Filters_PaddleOCR adding the possibility to detect the speed

The requirements are exactly the same as those indicated in the aforementioned project.

Downloaded the project, execute the pythom program

VIDEODetectSpeedInternationalLicensePlate_RoboflowModel_Filters_PaddleOCR.py


The test program VIDEODetectSpeedInternationalLicensePlate_RoboflowModel_Filters_PaddleOCR.py is only prepared to work with the attached Traffic IP Camera video.mp4 test video,
dowloaded from 
https://github.com/anmspro/Traffic-Signal-Violation-Detection-System/tree/master/Resources, 
since speed detection is performed over a region of the video, marked with a green rectangle, whose depth coincides with the length of a parking space that appears in the video and according to the following formula and parameters:

"""
          
         
           fps=25 #frames per second of video, see its properties

           fpsReal= fps/SpeedUpFrames # To speed up the process only one of SpeedUpFrames
                                      # is considered, SpeedUpFrames=5
           lengthRegion=4.5 #the depth of the considered region corresponds
                           # to the length of a parking space which is usually 4.5m

           Snapshots detected in the video region

           Speed (Km/hour)=lenthRegion * fpsReal * 3.6 / Snapshots

          Where 3.6 = (3600 sec./ 1 hour) * (1Km/ 1000m)
          
          This formula depends on the number of snapshots detected, which depends on the quality and speed of the plate detector, so in any case it has to be adjusted with practical tests in the field.

As a result, the console gets the following output:

AR606L Speed: 81.0Km/h  snapshots: 1

AR6061 Speed: 81.0Km/h  snapshots: 1

AE670S Speed: 81.0Km/h  snapshots: 1

A968B6 Speed: 81.0Km/h  snapshots: 1


In which it is verified that the speed is determined by the number of snapshots in the delimited region of interest and errors coming from false registration detections such as AR6061 that is a false registration of AR606 or not even detected plates as APHI88 and A3K961

Comparing  with the project https://github.com/ablanco1950/DetectSpeedLicensePlate_Yolov8_Filters_PaddleOCR the results seem worse as fewer snapshots are detected (safe from later adjustments)

A camera with more frames per second is needed, a computer  with better features and better license plate detection. And/or a routine that will detect similarities between two consecutive license plates and flag them as erroneous.

You also get a logging file VIDEOLicenseResults.txt with the detected license plates

and a summary file: VIDEOLicenseSummary.txt with the following fields:

- License detected
- number of snapshots in the region of interest
- time of first snapshot
- last snapshot time
- estimated speed

References:

https://github.com/amanraja/vehicle-speed-detection-

https://www.ijcseonline.org/pub_paper/124-IJCSE-06271.pdf

https://medium.com/@raja_8462/an-efficient-approach-for-vehicle-speed-detection-1fce82aacaf2

https://pypi.org/project/paddleocr/

https://learnopencv.com/ultralytics-yolov8/#How-to-Use-YOLOv8?

https://public.roboflow.com/object-detection/license-plates-us-eu/3

https://docs.ultralytics.com/python/

https://github.com/ablanco1950/DetectSpeedLicensePlate_Yolov8_Filters_PaddleOCR

https://medium.com/@chanon.krittapholchai/build-object-detection-gui-with-yolov8-and-pysimplegui-76d5f5464d6c

https://medium.com/@alimustoofaa/how-to-load-model-yolov8-onnx-cv2-dnn-3e176cde16e6

https://medium.com/adevinta-tech-blog/text-in-image-2-0-improving-ocr-service-with-paddleocr-61614c886f93

https://machinelearningprojects.net/number-plate-detection-using-yolov7/

https://github.com/ablanco1950/LicensePlate_Yolov8_MaxFilters

Filters:

https://gist.github.com/endolith/334196bac1cac45a4893#

https://stackoverflow.com/questions/46084476/radon-transformation-in-python