These steps are basically 1:1 with notes provided by Drew

- Some changes are not listed here so it would be best to clone if you want latest changes

## Basic step by step fixes
-/home/vboxuser/rock/slam/uwv_kalman_filters
with:

https://github.com/tomcreutz/slam-uwv_kalman_filters.git

-/home/vboxuser/rock/slam/orogen/uwv_kalman_filters
with:

https://github.com/tomcreutz/slam-orogen-uwv_kalman_filters.git

### fix time unit issues	
- /home/vboxuser/Desktop/rock/slam/orogen/uwv_kalman_filters/tasks/PoseEstimator.cpp
	- replace line 419:
	- base::Time current_sample_time = base::Time::fromMicroseconds(pose_filter->getLastMeasurementTime());
	- with: base::Time current_sample_time = pose_filter->getLastMeasurementTime();
	
- /home/vboxuser/Desktop/rock/slam/orogen/uwv_kalman_filters/tasks/VelocityProvider.cpp
	- replace old 247: base::Time current_sample_time = base::Time::fromMicroseconds(velocity_filter->getLastMeasurementTime());
	- with: base::Time current_sample_time = velocity_filter->getLastMeasurementTime();

amake

## (Advanced) Changes
- Added web socket to send messages of log samples in rigid body state format
- adding implementation to apriltag transformer functions

### Clone Method
- replace orogen folder with mine at

https://github.com/con169/slam-orogen-uwv_kalman_filters.git
