# MPC for Sensorless AO
[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Frlawlstjd960%2Fhit-counter&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://hits.seeyoufarm.com)

This repository is a `Matlab` implementation of the model predictive control of time-varying aberrations for sensorless adaptive optics from Jinsung~Kim et al. [[1]].
A schematic diagram of the sensorless AO system is shown below.

<img src="images/SensorlessAO_overview.png" />

Incoming light with time-varying phase aberration ![equation](https://latex.codecogs.com/png.image?\dpi{110}%20\phi_{\textrm{distort}}) caused by atmospheric turbulence is directed to the DM with a corrected wavefront ![equation](https://latex.codecogs.com/png.image?\dpi{110}%20\phi_{\textrm{cor}}).
The reflected beam with residual wavefront aberration ![equation](https://latex.codecogs.com/png.image?\dpi{110}%20\phi_{\textrm{res}}%20=%20\phi_{\textrm{distort}}%20+%20\phi_{\textrm{cor}}) is entered onto a scientific camera, such as a CCD or CMOS, to measure the PSF.
The estimator determines the Zernike coefficient constituting ![equation](https://latex.codecogs.com/png.image?\dpi{110}%20\phi_{\textrm{res}}) without using a wavefront sensor, based on the approximate model.
The controller computes the applied voltage to each actuator of the DM to correct the aberration of the newly incoming light.

The block diagram for `Matlab` simulation is represented as follow.

<img src="images/block_diagram.png" />

Before implementing this MATLAB code, you must install the appropriate MPC optimizer such as ***CVX, fmincon, fastMPC***.

***CVX*** which is a MATLAB package for specifying and solving convex optimization problem can be executed through the *cvx_setup* command after installing the package provided in [[2]].
***fmincon*** is a built-in function provided by MATLAB and does not need to be installed separately.
Lastly, ***fastMPC***, an algorithm that fixes the barrier parameters and Newton steps of the interior-point method, can be used to solve the resultant constrained optimal control problem in real time [[3]].



