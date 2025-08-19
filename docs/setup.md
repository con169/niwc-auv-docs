# Instructions for a new VM 

## Preface
Check out ROCK's [supported platforms](https://github.com/rock-core/rock-osdeps-package_set?tab=readme-ov-file) on the official rock-core repo. It seems the latest master-22.06 is only supported on Ubuntu 20.04 (Focal Fossa)

Also refer to https://www.rock-robotics.org/ to understand more about using commands in the ROCK framework.

Instead of grouping all the required packages you may need in one section, I want to keep them separate so someone setting this up will understand the sequence in which certain dependencies are needed

## (1) Standard initialization of new Linux OS
- Use any method to access Ubuntu 20.04
- `sudo apt update`
- `sudo apt upgrade`

### Install Ruby
`sudo apt-get install ruby ruby-dev wget build-essential`

## (2) Installing Rock for Ubuntu 20.04 
Make a 'rock' directory anywhere. I chose to make it in the home directory
``` shell
cd;
mkdir rock; cd rock;
wget -q https://raw.githubusercontent.com/rock-core/buildconf/master/bootstrap.sh
sh bootstrap.sh
```
- add env.sh to .bashrc
`source ~/[user]/rock/env.sh`

Inside your 'rock' directory,
```shell
cd ~/rock
aup
amake
```
`aup` fetches dependencies that were specified in your autoproject's manifest file

`amake` then builds the framework

### Install MTK and pose_estimation dependencies
These base libraries are needed for the computation needed for the Kalman Filter
```shell
sudo apt install libsuitesparse-dev libeigen3-dev libboost-all-dev
sudo apt-get install libgdal-dev
```


 in autoproj, modify manifest. Add this after "rock.core" in layout.
Be careful of indentation.
- slam/mtk
- slam/pose_estimation
- slam/uwv_kalman_filters
- slam/orogen/uwv_kalman_filters

aup, amake to check

## (3) Replacing fetched libraries that contain errors
Libraries: `perception/orogen/apriltags` and `slam/orogen/uwv_kalman_filters` both have build errors.
You can either refer to the in-depth documentation to fix them yourself or clone from my repos where I fixed the build errors from Tom Creutz's latest repos
### perception/orogen/apriltags
https://github.com/con169/perception-orogen-apriltags

Refer to full documentation fix [here](In-Depth/opencv_apriltags.md) for more in depth instructions and explanation. Otherwise, follow the readme seen on this repo.

### slam/orogen/uwv_kalman_filters
https://github.com/con169/slam-orogen-uwv_kalman_filters

Same instructions, replace folder and amake.

Refer to more in-depth [documentation](In-Depth/orogen_uwv_kalman_filters.md) for specific changes

amake in `~/rock/` and should be done