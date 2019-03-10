# Project: Kalman Filters

## Introduction
In this project I will write a Kalman Filter for a 2D simulated environment. The simulation consists of a car moving to the right on a road, and pedestrinas trying to cross this road. My Kalman Filter is important for self-driving cars, as it going to make sure we don't hit (or at least minimize the number of hits on) the pedestrians.

## Tasks
Write Kalman Filter to track the people crossing the road in a coordinate system with (0, 0) centered on the robot. Since we are only tracking the pedestrians relative to this refrence frame, there is no need to do localization on the car itself. All measurements are also given in this frame (so don't have to worry about converting measurements to different reference frames). All of this work will be done in `kalmanfilter.py` file. Specifically, the tasks are the following.

### Step 1: Creating the Matrices

**A**: This is the state update transfomration matrix. Essentially, given our old state, what will our new state probably look like? This matrix should perform the operations required to get there. In this project, our state is going to be a 4x1 matrix with `pos_x`, `pos_y`, `vel_x`, and `vel_y`.

**B**: This is our control signal transformation matrix. As you may remember, this matrix takes in a control signal, and returns the vector (in the same shape as your state) that represents how the control signal changes your state. A control signal for this problem may be unintuitive, since we are tracking pedestrians, not a car, and we won't be able to get a "control signal" from the pedestrians. However, our car will accelerate to avoid hitting pedestrians, which will give the pedestrians an *apparent* acceleration in the opposite direction. Because of this you can use acceleration information from the car as a control signal for the pedestrians.

**C**: This is transformation matrix from your state space to the measurement space. Essentially, this matrix will convert a state into an expected measurement. We will be measuring x and y position.

Matrices **R**, **Q**, and **I** are provided as real experiment.

### Step 2 - 3: Prediction and Measurement Updates

In `kalmanfilter.py`, the `prediction(control_signal)` and `measurement(measurements, Q)` functions are updated.

## Testing

For visual inspection, please run `python sim.py`. The red ovals/dots represent the states + covariances of all the people currently being tracked by the Kalman Filter.
In the short video given, the car slows down, stops or changes direction to avoid the perdestrian