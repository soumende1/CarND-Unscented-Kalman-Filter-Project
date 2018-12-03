# Unscented Kalman Filter Project Starter Code
Self-Driving Car Engineer Nanodegree Program

In this project utilize an Unscented Kalman Filter to estimate the state of a moving object of interest with noisy lidar and radar measurements. Passing the project requires obtaining RMSE values that are lower that the tolerance outlined in the project rubric. 

This project involves the Term 2 Simulator which can be downloaded [here](https://github.com/udacity/self-driving-car-sim/releases)

This repository includes two files that can be used to set up and intall [uWebSocketIO](https://github.com/uWebSockets/uWebSockets) for either Linux or Mac systems. For windows you can use either Docker, VMware, or even [Windows 10 Bash on Ubuntu](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/) to install uWebSocketIO. Please see [this concept in the classroom](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/0949fca6-b379-42af-a919-ee50aa304e6a/lessons/f758c44c-5e40-4e01-93b5-1a82aa4e044f/concepts/16cf4a78-4fc7-49e1-8621-3450ca938b77) for the required version and installation scripts.

Once the install for uWebSocketIO is complete, the main program can be built and ran by doing the following from the project top directory.

1. mkdir build
2. cd build
3. cmake ..
4. make
5. ./UnscentedKF

Tips for setting up your environment can be found [here](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/0949fca6-b379-42af-a919-ee50aa304e6a/lessons/f758c44c-5e40-4e01-93b5-1a82aa4e044f/concepts/23d376c7-0195-4276-bdf0-e02f1f3c665d)

Note that the programs that need to be written to accomplish the project are src/ukf.cpp, src/ukf.h, tools.cpp, and tools.h

The program main.cpp has already been filled out, but feel free to modify it.

Here is the main protocol that main.cpp uses for uWebSocketIO in communicating with the simulator.


INPUT: values provided by the simulator to the c++ program

["sensor_measurement"] => the measurment that the simulator observed (either lidar or radar)


OUTPUT: values provided by the c++ program to the simulator

["estimate_x"] <= kalman filter estimated position x
["estimate_y"] <= kalman filter estimated position y
["rmse_x"]
["rmse_y"]
["rmse_vx"]
["rmse_vy"]

---

## Prerequisites - Important Dependencies
The project has the following dependencies (from Udacity's seed project):

* cmake >= 3.5
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
  * make >= 4.1 (Linux, Mac), 3.81 (Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
  * gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

## Compiling and Executing the Project

1. Clone this repo.
Note that the algorithm is captured in the following programs src/ukf.cpp, src/ukf.h, tools.cpp, and tools.h
The program main.cpp has already been filled out in starter code and is being reused here

2 - Open Ubuntu. Change the working directory to the working folder

3. In the working directory, Compile the code: `cmake . (one dot) && make`

![here is the Ubunto termina](./images/starting_position.PNG)

4. Run it using: `./UnscentedKF` 

5 Open the simulator. The output should be
<code> Listening to port 4567
       Connected!!!
 </code>

6 Click the start/Restart button of the simulator

## Editor Settings

We've purposefully kept editor configuration files out of this repo in order to
keep it as simple and environment agnostic as possible. However, we recommend
using the following settings:

* indent using spaces
* set tab width to 2 spaces (keeps the matrices in source code aligned)

## Code Style

Please stick to [Google's C++ style guide](https://google.github.io/styleguide/cppguide.html) as much as possible.

## Generating Additional Data

This is optional!

If you'd like to generate your own radar and lidar data, see the
[utilities repo](https://github.com/udacity/CarND-Mercedes-SF-Utilities) for
Matlab scripts that can generate additional data.

## Project Instructions and Rubric

### Compiling
Your code should compile.
No modifications on CMakeList.txt were done in this project. It compiles without errors or warnings.


### Accuracy
the code was run with the simulator
The UKF accuracy was:

Dataset 1 : RMSE = [0.0690, 0.0846, 0.3348, 0.2909]

Dataset 2 : RMSE = [0.0977, 0.0655, 0.6421, 0.2657]

### Following the Correct Algorithm
Your Sensor Fusion algorithm follows the general processing flow as taught in the preceding lessons.

The UKF implementation could be found at  [src/ukf.cpp line 13](./src/ukf.cpp#L13). On the ProcessMeasurement method, the Prediction is executed for the prediction step [src/ukf.cpp line 196](./src/ukf.cpp#L196), and methods UpdateRadar [src/ukf.cpp line 354](./src/ukf.cpp#L354) and UpdateLidar [src/ukf.cpp line 322](./src/ukf.cpp#L322)are executed for the update step depending on the measurement type.

### Your Kalman Filter algorithm handles the first measurements appropriately.
The first measurement is handled at ProcessMeasurement from line 103 [src/ukf.cpp](./src/ukf.cpp#L103)

### Your Kalman Filter algorithm first predicts then updates.
The prediction step is implemented at Prediction method from line 196 [src/ukf.cpp](./src/ukf.cpp#L196)

### Your Kalman Filter can handle radar and lidar measurements.
Different type of measurements are handled in two places in UKF class:

The Radar measurement in handled in line 354 [src/ukf.cpp](./src/ukf.cpp#L354)
The Lidar measurement is handled in line 322 [src/ukf.cpp](./src/ukf.cpp#L322)

![here is the screenshot with data set 1] 
(./images/run_dataset1.PNG)

![here is the screenshot with data set 2]
(./images/run_dataset2.PNG)





