# 使用 kalman 目标跟踪

## 一、简介

#### 	封装好的函数:

```matlab
function kalmanFilterForTracking
```

```matlab
This example is a function with its main body at the top and helper routines in the form of nested functions.
这个例子是一个函数，它的主体在顶部，辅助例程以嵌套函数的形式出现。
```

#### 	检测:

```matlab
showDetecttions();
```

#### 	显示轨迹:

```matlab 
showTrajectory();
```

## 二、单目标跟踪

```matlab 
function trackSingleObject
```

​		通过配置函数 

```matlab
configureKalmanFilter 
```

```matlab
% The |configureKalmanFilter| function returns a Kalman filter object. You
% must provide five input arguments.
%
%   kalmanFilter = configureKalmanFilter(MotionModel, InitialLocation,
%            InitialEstimateError, MotionNoise, MeasurementNoise)
```

​	创建

```matlab
vision.KalmanFilter 
```

#### 顶层变量（用于顶层函数间传递参数）：

```matlab 
frame          	= []; 	% A video frame
detectdLocation = [];	% The detected location
trackedLocation = [];	% The tracked location
label      		= '';	% Lable for the ball
utilities 		= [];	% Utilities used to process the cideo
```

### Single Object Track Procedure：

```matlab
function trackSingleObject(param)
	% Create utilites used for reading video,detectin moving objects,
	% and dispalying the results.
	utilites = createUtilities(param);
	
	isTrackInitialized  = false;
	while hasFRame (utilities.videoReader)
		frame = readFrame(utilities.videoReader);
		
		% Detect the ball.
		[detectedLocation,isObjectDetected] = detectObject(frame);
		
		if ~isTrackInitialized 
			if isObjectDetected 
                % Initalize a track by creating a Kalman Filter when the ball is
                % detected for the first time.
                initialLocation = computeInitialLocation(param,detectedLocaion);
                kalmanFilter = configureKalmanFilter(param.motionModel,
                    param.initialLocation,param.initialEstimateError,
                    param.motionNoise,param.measurementNoise);

                isTrackInitialzed = true;
                trackedLocatin = correct(kalmanFilter,detectedLocation);
                label = 'Initial';
			else
                trackedLocation = [];
                label = '';
			end
		else
			% Use the Kalman filter to track the ball.
			if isObjectDetected % The ball was detected.
                % Reduce the measurement noise by calling predict followed by correct.
                predict(kalmanFilter);
                trackedLocation = correct(kalmanFilter,detectedLocation);
                label = ‘Corrected’;
			else % The ball was missing.
            	% Predic the ball's location.
            	trackedLocation = predict(kalmanFilter);
            	label = 'Predicted';
            end
         end
         
         annoateTrackedObject();
       end % whlie

	showTrajecttory();
end			
```

```matlab
param = getDefaultParameters();	% get kalman configuration that works well
								% for this example
								
trackSingleObject(param);		% visualize the results
```









