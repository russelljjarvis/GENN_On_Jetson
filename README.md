# JetsonKnightPotjans
A Basic Guide for configuring the Nvidia Jetson Nano for running the GENN Potjan et al cortical models developed by Knight et al.

### Step 1.
Acquire an Nvidia Jetson Nano (developer) there are two memory options buy the one with the greatest amount of memory (4GB).
### Step 2.
Download and install the Balena Etcher tool suitable for your operating system https://www.balena.io/etcher/. 
Flash the latest Jetpack to the SD Card this guide will only work for >=jetpack 4.6, and has only been tested for 4.6
https://developer.nvidia.com/embedded/jetpack
Use Bletcher to flash the jetpack-4.6
### Step 3.
Insert the flashed image into the Jetson, log in to the Jetson.
Git is already installed with Jetpack 4.6
In the terminal run:
```
git clone https://github.com/genn-team/genn
cd genn
```

