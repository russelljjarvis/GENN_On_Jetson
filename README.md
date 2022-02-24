

# Jetson Knight Potjans



<p align="center">
  <a href="#Description">Description</a> •
  <a href="#Motivation">Motivation</a> •
  <a href="#User Experience">Install</a> •
  <a href="#Step 1">Plans</a> •
  <a href="#Step 2">Flow Chart</a> •
  <a href="#TODO">Why Not Optimize Small SNNs With Bigger SNNs</a>
</p>

<p align="center">
  
 # Description
This is a basic Guide for configuring the Nvidia Jetson Nano for running the GENN Potjan et al cortical models developed by Knight et al.


## Motivation 
The nvidia Jetson nano is a cheap ($249 AUD) development board that comes with a modest Nvidia GPU. The Jetson nano enables people to develop execute and test GPU compliant code on affordable local resource. Additionally the Jetson Nano may consume significantly less electricity than large workstations. 

Neuromorphic hardware is theoretically a great platform for simulating cortical models but it is currently not available to hobbiests. Access to Neuromorphic hardware requires a formal application, however the Nvidia Jetson Nano is an affordable product available at a small cost. A model of cortex developed by Knight was implemented using Cpp/CUDA technologies on GPU hardware, this model has been re-designed to run at an increasing large scale and only the smaller version of the model has been tested here.

## User Experience
These steps ran surprisingly smoothly for me but note I deliberately worked from a fresh jetpack install and I declined package updates. From my experience Jetson CUDA environments and dependencies can deteriate very rapidly if you try to install various different packages and make too many environmnental changes. Its almost worth having a seperate SD card for different projects.

### Step 1.
Acquire an [Nvidia Jetson Nano](https://developer.nvidia.com/embedded/jetson-nano-developer-kit) (developer) there are two memory options buy the one with the greatest amount of memory (4GB).
### Step 2.
Download and install the Balena Etcher [tool](https://www.balena.io/etcher/) suitable for your operating system. 
Flash the latest Jetpack to the SD Card this guide will only work for >=[Jetpack 4.6](https://developer.nvidia.com/embedded/jetpack), and has only been tested for Jetpack 4.6
Use Etcher to flash the jetpack-4.6
### Step 3.
Insert the flashed image into the Jetson, log in to the Jetson.

Git is already installed with Jetpack 4.6
CUDA Toolkit is already installed when on Jetpack 4.6 although you may be prompted to agree to the licence when you first log in to the Jetson.

### Step 4
The rest is very loosely based on the instructions for installing [genn](https://github.com/genn-team/genn).

### Step 5
#### For future reference make a note to inform your compiler where CUDA lives.

In the terminal run:
```
echo "export CUDA_PATH=/usr/local/cuda" >> ~/.bashrc
echo "export PATH=$PATH:$CUDA_PATH/bin" >> ~/.bashrc
```
### Step 6
#### Install the GENN source code
Now run:
```
git clone https://github.com/genn-team/genn # obtain the genn source code
cd genn # enter the directory of the genn code
echo "export PATH=$PATH:/home/me/genn/bin" >> ~/.bashrc
source ~/.bashrc
```
### Step 7
#### Use GENN to compile the Potjans model
If you are still in the genn directory:
```
cd /userproject/PotjansMicrocircuit_project
make #compiles the Potjans model
```
#### Step 8
#### Run the model
This final step runs the compiled binary of the Potjans model, you can configure the model itself too, before compiling it.

```
./generate_run test
```

The model runs and spike times are recorded to disk. The model executes in a timely fashion.

#### TODO

Use the tool `jtop` and or `tegrastats` (built in) to profile the Jetson's GPU and to confirm that the GPU is experiencing full utilization.

