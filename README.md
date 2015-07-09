#INTRODUCTION

This class provides a simple low-pass filter to deal with noisy accelerometer signals for cocosd-x version 3.
It's a straight port of the analogous filter found in the [AccelerometerGraph example](https://developer.apple.com/library/ios/samplecode/AccelerometerGraph/Introduction/Intro.html)
found in the iOS developer library.

#Usage
Include the AccelerometerFilter.h and AccelerometerFilter.cpp in your project.
Include and initialize an instance variable for each scene in your project that uses the accelerometer.
The constructors takes a reference to the -scene- and the value of the desiderd -cutoff Frequency-.
Higher values of the cutoff frequency result in a smoother but also more lagged signal.

The -setMaxThreshold- and -setMinThreshold- methods can be used to clamp the accelerometer values to given values.
Use the -getAcceleration- method to get the actual filtered value.

#Example code

std::unique_ptr<AccelerometerFilter> accelerometer;
accelerometer=make_unique<AccelerometerFilter>(-scene-,-cutoff Frequency-);
accelerometer->setMinThreshold(0.1, 0.1, 0.1);
accelerometer->setMaxThreshold(0.4, 0.4, 0.4);

CCLOG("Acc x:%f",accelerometer->getAcceleration().x);
CCLOG("Acc y:%f",accelerometer->getAcceleration().y);