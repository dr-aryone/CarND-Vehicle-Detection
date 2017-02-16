## Vehicle Detection
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)


The goals / steps of this project are the following:

* Perform a Histogram of Oriented Gradients (HOG) feature extraction on a labeled training set of images and train a classifier Linear SVM classifier
* Optionally, you can also apply a color transform and append binned color features, as well as histograms of color, to your HOG feature vector. 
* Note: for those first two steps don't forget to normalize your features and randomize a selection for training and testing.
* Implement a sliding-window technique and use your trained classifier to search for vehicles in images.
* Run your pipeline on a video stream (start with the test_video.mp4 and later implement on full project_video.mp4) and create a heat map of recurring detections frame by frame to reject outliers and follow detected vehicles.
* Estimate a bounding box for vehicles detected.

Here are links to the labeled data for [vehicle](https://s3.amazonaws.com/udacity-sdc/Vehicle_Tracking/vehicles.zip) and [non-vehicle](https://s3.amazonaws.com/udacity-sdc/Vehicle_Tracking/non-vehicles.zip) examples to train your classifier.  These example images come from a combination of the [GTI vehicle image database](http://www.gti.ssr.upm.es/data/Vehicle_database.html), the [KITTI vision benchmark suite](http://www.cvlibs.net/datasets/kitti/), and examples extracted from the project video itself.   You are welcome and encouraged to take advantage of the recently released [Udacity labeled dataset](https://github.com/udacity/self-driving-car/tree/master/annotations) to augment your training data.  

Example of Vehicle data:-

![Vehicle](assets/VehicleEg.JPG)

#Hog
Here I have used skimage's hog method. This has been implemented in `hog_features` function in third cell of jupyter notebook(CarND-Vehicle-Detection.ipynb).
I tried various permutations and combinations and got high accuracy for YUV color space with orientation=8,pixels per cell = 8
and cells per block = 2.I have taken hog of each channel and then concatenated them.

Example of Non-Vehicel data:-
![NonVehicle](assets/NonVehicleEg.JPG)

#Classifier
The HOG features extracted from the training data using the `derive_features` function in cell four.Then I normalized the data using sklearn.preprocessing's `StandardScaler`.This has been implemented in cell 10.
After normailzing I split my data into training and test using `train_test_split` of sklearn.model_selection.
I have used Linear SVM as classifier. We attained accuracy of 98.5%.

#Sliding Window Search
