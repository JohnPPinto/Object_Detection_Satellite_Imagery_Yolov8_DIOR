# Object_Detection_Satellite_Imagery_Yolov8_DIOR
Building a Yolov8n model from scratch and performing object detection in optical remote sensing images.

## Repo Structure
* Complete code is in the notebook - [dior_object_detection_satellite_imagery_yolov8.ipynb](https://github.com/JohnPPinto/Object_Detection_Satellite_Imagery_Yolov8_DIOR/blob/main/dior_object_detection_satellite_imagery_yolov8.ipynb)
* All the model results are in the "runs" directory.

## Introduction
Deep learning is improving every day and multiple different neural network architectures are being built in computer vision. These models are capable of classifying, detecting, tracking and segmenting, but there is one place where improvement is needed is in Remote Sensing Images or Satellite Imagery. Here the biggest problems come down to natural scene images vs satellite imagery, they come down to the way the images are represented, the difference comes down to the satellite images where the information of the objects is only the overhead part, the roof of the object while the natural scene images have all sort of information from different directions. In satellite images, the edges of the object give a lot of information in object representation but this can even confuse the model, there are even shadows, different season, and different time of day and night that affects the brightness and contrast, then there's even the altitude from where the image has been taken this all affect the images' condition. So, all-in-one satellite images are really tough for any model in computer vision.

## Objectives
* The main objective of this project is to build a model that is capable of classifying and detecting multiple different objects in a Satellite Imagery/Optical Remote Sensing image.
* Another objective is to test the latest Yolo model (Yolo V8) capabilities.

## Dataset
* For this project I will be using the DIOR dataset. 
* This dataset contains 20 different classes, which are a mix of tiny to large-scale objects.
* There are in total 23, 463 images which are split for 50% train and test sets.
* The images are randomly shuffled and are of high quality 800 x 800 px.
* There are some shortcomings like missing annotation for some objects and uneven split object-wise.

## Data Preprocessing
Preprocessing was mainly done for the annotation, the original annotation is in the format of Pascal VOC, a .xml file which does not work with the Yolo model. For this, the annotation files were converted to .txt files in Yolo format.

The splits were originally 50% train and 50% test which were not favorable, I made a few changes by keeping the 50% train for only training and splitting the test dataset to 20%-80% for validation and testing dataset.


## Model Training and Testing
* I have used the Yolov8n model by Ultralytics for this project - Github [link](https://github.com/ultralytics/ultralytics).
* I have trained the Yolo model for 50 epochs from scratch for this custom dataset for a batch size of 16 and keeping the image size as the original size of 800px.
* I didn't change the image size because compressing the image will result in loss of data and the objects are already on a small scale this will degrade the quality of the object and the overall dataset will be in bad condition.
* Testing of the model was done on 9391 images.
* Model showed good results: 0.71 for mAP50 and 0.485 for mAP50-95.
* You can check the notebook and the runs directory for complete code and model results.
* Other than the testing on the dataset, I took a clip of google earth to test the model on video files. Below are the results:
 


https://user-images.githubusercontent.com/66053973/233864714-701112ea-af8c-4904-86be-33c626706404.mp4



https://user-images.githubusercontent.com/66053973/233864742-2f57b074-beda-4213-9a75-029c31d1b221.mp4

## Conclusion
Yolov8 is fast and capable. The best part is that it is lightweight, which helps in running on cheaper GPU's much easier. For me, training more than 20,000 images on A4000 was smooth, it took less than 2 and half hours to train the model. This is good, using a tiny dataset and a quick experimentation is possible with Yolov8.

The DIOR dataset is a large dataset and contains really good quality images. Results can be improved by merging the whole dataset and conducting smaller and controlled experiments with different model size of the Yolov8. I have used only the lightest and smallest model there are 4 more models that get bigger and heavier.

## References
* Model Docs: https://docs.ultralytics.com/
* Dataset links and paper: https://drive.google.com/open?id=1UdlgHk49iu6WpcJ5467iT-UqNPpx__CC and https://www.sciencedirect.com/science/article/abs/pii/S0924271619302825
