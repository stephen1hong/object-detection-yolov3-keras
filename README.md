# object-detection-yolov3-keras

*Environments

 * python 3.6
 * tensorflow 1.14.0
 * keras 2.1.5
 * GPU (GTX 1070)
 * OpenCV 4.1.1
 * ubuntu 16.0.4
 
*Usage
 1. download yolo3.weights and yolov3.cfg from Internet
 2. run "convert.py  -w yolov3.cfg yolov3.weights model_data/yolo_weights.h5"
 3. generate your own annotation (e.g., train.txt) in the current project folder for your own dataset
   with annotation format:
     * for single object in an image: path/to/img.jpg box_left,box_top,box_right,box_bottom,class_label (Note a space between .jpg file and box_left and no space betwen ",")
     * for multiple objects in an image: path/to/img.jpg box1_left,box1_top,box1_right,box1_bottom,class_label box2_left,box2_top,box2_right,box_bottom,class_lebel (Note a space between class_label and box2_left) 
 4. generate a class name file and place it into model_data folder
    * For single object, class_label set as 0, class_name.txt containing the single object name
    * For multiple objects, class_label set as 0, 1, ..., class_name.txt containing names of the objects
 5. generate your anchlor box estimates on your training dataset by running: python kmeans.py
 6. model training:  python train.py 
    * On our case of a single object detection, for 500 images in training set with 20% or 10% for validation set, the training on GPU (GTX1070) was stoped at about 100 epochs with initial learnign rate of 1e-4. You need to adjust hyperparameters according to your case. 
 7. model testing:  python image_detect.py
 
  reference: qqwweee/keras-yolo3
 
