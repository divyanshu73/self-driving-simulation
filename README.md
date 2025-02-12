# Self Driving Car on Udacity Simulation

The purpose of this repository is to implement the Nvidia `End to End Learning for Self-Driving Cars` paper and train a CNN model to control an autonomous car steering angle which further tested on Udacity Simulation.

## Videos showing Successful Model

### Autonomous Driving on New Track
https://github.com/user-attachments/assets/5011269c-d500-4ca9-abb6-b59424664794

## Model Training

The file `self_driving_model_training.ipynb` does the following:

### 1. Download, store, and clean data from manual drives

The program first retrieves csv data representing the `steering angle`, `throttle`, `reverse` and `speed`, as well as the images corresponding camera images (left, center and right). The program then cleans and unbiases the data. The data comes from manual drives stored at https://github.com/tylerlum/self-driving-car-data-track-1

![alt text](images/Unbias_Data.png?raw=true "Unbias Data")

### 2. Perform augmentation techniques on images to improve the dataset

To improve the robustness of the model, the program uses augmentation techniques to vary the dataset. These include:

#### Zoom

Zooms into the image.
![alt text](images/Zoom.png?raw=true "Zoom")

#### Pan

Translate the image.
![alt text](images/Pan.png?raw=true "Pan")


#### Brightness

Varies brightness of image. Mostly darkens, as it proved more effective for the model.
![alt text](images/Brightness.png?raw=true "Brightness")

#### Random Augmentation

The program augments images in a random distribution to ensure that variety is preserved.

![alt text](images/Random_Augmentation.png?raw=true "Random Augmentation")

### 3. Preprocess images

Next, the program converts the RBG images to YUV images, which have proven very effective for Nvidia models.

![alt text](images/Preprocess.png?raw=true "Preprocess")

![alt text](images/Preprocess_Augmentation.png?raw=true "Preprocess+Augmentation")

### 4. Create and saves a Nvidia model

The program then creates a Nvidia model, based on the following diagram.

![alt text](images/Nvidia_Model.png?raw=true "Nvidia Model")

 
A file called `<name>.h5` will be saved, which stores the trained and validated Nvidia model.

## How to Use Model

The model file can then be used in the following procedure.

### 1. New Enviroment

Create the new enviroment in your local and install the prerequisites from `requirements.txt`
  
### 2. Use Model File

Ensure that `<name>.h5` is in the same directory as `drive.py`. Then edit the `drive.py` source code to replace the line

```
model = load_model('<name>.h5')
```

and adjust `speed_limit` to any number between 0 and 30.

### 3. `drive.py`

Run the following from Anaconda Prompt + download any dependencies that come up.

```
python drive.py
```

### 4. Starting the Self Driving Car Simulator in Autonomous Mode

Install the Self Driving Car Simulator (Version 1) from: https://github.com/udacity/self-driving-car-sim and run the program. Then start the Autonomous mode in either track.


