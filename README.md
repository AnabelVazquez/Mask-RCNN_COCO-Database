# Introduction

The principal project in which I´m currently working consist on process eye fundus images. 

I start from a video, then this video is converted into frames in which we can detect eye fundus segments. The next steps will be reconstruct a whole eye fundus image to process it.

But first of all, a Neural Network which can label this eye fundus segments in needed. So I got inspired by @wkentaro to label my dataset with labelme (https://github.com/wkentaro/labelme) and I got inspired by @soumik12345 to use Mask-RCNN to detect objects in a photo (https://github.com/soumik12345/geekyrakshit-blog/blob/master/_notebooks/2020-04-13-detectron-mask-rcnn.ipynb).

In this repository I'll show you how we can adapt Mask-RCNN to detect eye fundus segments using my own dataset of training and test, and using COCO dataset to train de model.

# Steps:

1. Select enough images to train the model and create 2 dataset: train and test. In my case they are called "DatasetTraining" and "DatasetTest"
DatasetTraining contains 307 Images and DatasetTest contains 76 Images.

2. Label all the images of both folders with labelme.

3. Create COCO file from this annotations using labelme2coco [look the script called "labelme2coco_GitHub.ipynb"].

4. Download the script called "Mask-RCNN_GitHubVersion.ipynb", change directories and start training your model

# Explanation:

@soumik12345 used Mask-RCNN with another type of Json file which is not COCO file. He/She transform his/her dataset into another format with the function "def get_balloon_dicts(img_dir):" and this new format is used in the rest of the code. 
Hence I need to modify this function to tranform my COCO dataset into the same format he/she obtain finally. Therefore I develop the function "def Get_EyeFundus_Data(image_dir):".

# Files that I uploaded:

1. Dataset folders: They contain images of my own eye, thus avoiding data protection problems.

2. The folder which contains the results of the model (It is called "output")

3. Two scripts: 
- "labelme2coco_GitHub.ipynb"
- "Mask-RCNN_GitHubVersion.ipynb"
