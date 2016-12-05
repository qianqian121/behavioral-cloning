# Behavioral Cloning

This project was created as an assessment for the [Self-Driving Car Nanodegree](https://www.udacity.com/course/self-driving-car-engineer-nanodegree--nd013) Program by Udacity. The goal is to drive a car autonomously in a simulator using a deep neuronal network (DNN) trained on human driving behavior. For that Udacity provided the simulator and a basic python script to connect a DNN with it. The simulator has two mode. In the "training mode" the car can be controlled through a keyboard or a game pad to generated data. More information about the data and it's structure can be found in the corresponding [section](https://github.com/pkern90/behavioral-cloning/blob/master/README.md#data). In the "autonomous mode" however the car receives it input commands by the python script.

The following animations shows the final model controlling the car on both tracks.

Track 1                       |  Track 2
:----------------------------:|:------------------------------:
![Track 1](images/track1.gif) | ![Track 2](images/track2.gif)


# Getting Started
## Prerequisites

This project requires **Python 3.5** and the following Python libraries installed:

- [NumPy](http://www.numpy.org/)
- [SciPy](https://www.scipy.org/)
- [matplotlib](http://matplotlib.org/)
- [pandas](http://pandas.pydata.org/)
- [TensorFlow](http://tensorflow.org)
- [Keras](https://keras.io/)
- [h5py](http://www.h5py.org/)

Only needed for driving in the simulator:

- [flask-socketio](https://flask-socketio.readthedocs.io/en/latest/)
- [eventlet](http://eventlet.net/)
- [pillow](https://python-pillow.org/)


## Run The Drive Script

The drive script needs the path to the model definition as argument. The definition has to be a json file generated by Keras. In addition the model weights have to be located at the same path like the model definition and has to have the same filename (except file type of course). So if all the nessasary files (drive.py, model.json, model.h5) are in the same directory, the script can be executed with the following command:

```
python drive.py model.json
```
The script will automaticaly connect to the simulator and send commands as soon as it's entering the autonomous mode.

## Retrain The Model
# Structure
## Data

During "training mode" the simulator records three images with a frequency of 10hz. Next to a camera centered at the car there are also two additional cameras recording with an offset to the left and right respectively. This allows to apply an approach described in a [paper by Nvidia](https://arxiv.org/abs/1604.07316). A sample of the recorded images is shown in the following table:

Left                                   |  Center                                   |  Right
:-------------------------------------:|:-----------------------------------------:|:-------------------------------------:
![Sample Left](images/left_sample.jpg) | ![Sample Center](images/center_sample.jpg)|![Sample Left](images/right_sample.jpg)

Beside the images the the simulator also creates a log file while recording containing information like the current steering angle, speed and the corresponding image paths. In the displayed image an extract of the log file can be seen, containing all the features.

![Sample Log](images/sample_log.png)

## Model

<a href="https://raw.githubusercontent.com/pkern90/behavioral-cloning/master/images/model_wide.png" target="_blank"><img src="images/model_wide.png"></img> </a>
