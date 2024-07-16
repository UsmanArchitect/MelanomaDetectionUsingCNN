# Project Name
> To build a CNN based classification model to accurately detect Melanoma from the input images. 


## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Conclusions](#conclusions)
* [Acknowledgements](#acknowledgements)

<!-- You can include any other section that is pertinent to your problem -->

## General Information
To build a CNN based model which can accurately detect melanoma. 
Melanoma is a type of cancer that can be deadly if not detected early. 
It accounts for 75% of skin cancer deaths. 

A solution that can evaluate images and alert dermatologists about the presence of melanoma 
has the potential to reduce a lot of manual effort needed in diagnosis.

The model is trained for 9 different categories of images using 2239 images in train data and 118 images in validation data set
1. pigmented benign keratosis    
2. melanoma                      
3. basal cell carcinoma          
4. nevus                         
5. squamous cell carcinoma       
6. vascular lesion               
7. actinic keratosis             
8. dermatofibroma                
9. seborrheic keratosis          


## Conclusions
1. Able to build the model using CNN classification model using Keras Tensorflow library.
2. Prepared 3 models with base data and handled class imbalance through augmentation using Augmentor library by adding 500 samples per class.
3. Models are implemented using image size 180x180 using 32 as bach size using 80:20 split for training data using google colab.
4. Below topology is used for CNN model using optimizer="adam", activation = "relu", loss=SparseCategoricalCrossentropy 
4a: Model1 (Trainable parametrs = 3989801): (using resize and rescale regularization)
	Input Layer       --> Conv L1  --> 	Conv L2    --> 	Conv  L3   --> Dense Layer --> Output Layer
	32 x 180 x 180 x 3    16 x 3        32 x 3			64 x 3 			128				9
	
	Training Accuracy = 85% with Training loss = 0.38
	Validation Accuracy = 51% with Validation loss = 0.52
	Conclusion: Overfitting

4b: Model2 (Trainable parametrs = 3989801): (using data augmentation by random rotation(0.1) and random zoom(0.1) using dropout(0.2%) )
	Input Layer       --> Conv L1  --> 	Conv L2    --> 	Conv  L3   --> Dropout 	--> Dense Layer --> Output Layer
	32 x 180 x 180 x 3    16 x 3        32 x 3			64 x 3 			0.2			128				9
	
	Training Accuracy = 62% with Training loss = 1.05
	Validation Accuracy = 55% with Validation loss = 1.3
	Conclusion: Overfitting is reduced, but scope is present to improve validation accuracy

4c: Model3 (Trainable parametrs = 3990281): (using data augmentation by handling class imbalance by adding 500 samples using augmentor library 0.2.12 and batcNormalization after each layer)
	Input Layer       --> Conv L1  --> 	Conv L2    --> 	Conv  L3   --> Dropout 	-->Dense Layer --> Output Layer
	32 x 180 x 180 x 3    16 x 3        32 x 3			64 x 3 			0.2		   128				9
	
	Training Accuracy = 99.9% with Training loss = 0
	Validation Accuracy = 82.6% with Validation loss = 0.74
	Conclusion: Model accuracy improved both on training and validation and loss are minimized on both training and validation data.


<!-- You don't have to answer all the questions - just the ones relevant to your project. -->


## Technologies Used
- library - Tensorflow - 0.2 
- library - Augmentor-0.2.12
- library - Keras

<!-- As the libraries versions keep on changing, it is recommended to mention the version of library used in this project -->

## Acknowledgements
Give credit here.
- This project was inspired by my child 
- References if any...
- This project was based on [this tutorial](https://www.tesorflow.org).


## Contact
Created by [@UsmanArchitect] - feel free to contact me!


<!-- Optional -->
<!-- ## License -->
<!-- This project is open source and available under the [... License](). -->

<!-- You don't have to include all sections - just the one's relevant to your project -->