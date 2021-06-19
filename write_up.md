# PID Controller
Given a driving simulator which provides the cross track error(CTE) and the velocity(mph).  
- The goal of this project is to develop a PID controller in C++ that successfully drives the vehicle around the track.
- In order to navigate the car, I implemented 2 PID controllers.
- One for steering angle control and the other for speed control.

# Tuning
The most important part of the project is to tune the hyperparameters. This can be done by different methods such as manual tuning, Zieglor-Nichols tuning, SGD, Twiddle. I have done manual tuning.  
Manual tuning is hard but, the process of tuning help us better understand every single effect of PID parameters.

1. Proportional (P):  
    This parameter controls the error proportionally.  
    Increasing the proportional gain has the effect of proportionally increasing the control signal for the same level of error.  
    Setting only P control is agressiv e and has oscillations.

2. Integral (I):  
    This parameter controls the accumulating error. Addition of this term reduces the steady state error.  
    If there is a bias in the system, the integrator builds and builds, thereby increasing the control signal and driving the error down.

3. Derivative (D):  
    This parameter controls the rate of change of error.  
    Addition of this term reduces the oscillary effect in the system.  
    With derivative control, the control signal can become large if the error begins sloping upward, even while the magnitude of the error is still relatively small.  
    This anticipation tends to add damping to the system, thereby decreasing overshoot.


    ## Process of tuning
    The following approach is a best to tune manually:
    - Step 1) Set all gain(Kp, Ki, Kd) to zero.
    - Step 2) Increase the P gain(Kp) until the response to a disturbance is steady oscillation.
    - Step 3) Increase the D gain(Kd) until the oscillations go away (i.e. it's critically damped)  
    - Step 4) Repeat step 2&3 with increasing the D gain until it make stop the oscillations.
    - Step 5) Set Kp and Kd to the last stabel values.
    - Step 6) Increase the I gain(Ki), until it brings you to the setpoint with the number of oscillations desired.

    ## Final parameters
    The final parameters for my contoller are:

    |       | Steer | Speed |
    |:-----:|:-----:|:-----:| 
    | Kp    | 0.13  | 0.1   | 
    | Ki    | 0.001 | 0.002 |
    | Kd    | 2.0   | 1.0   |


    