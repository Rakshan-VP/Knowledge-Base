#type/method #domain/robotics #status/learning #scope/intermediate 
> [!abstract] Summary 
> IMU calibration compensates for accelerometer bias, scale and misalignment errors, gyroscope zero-rate bias, and the quadcopter's physical level offset. The calibrated measurements are then used by the attitude-estimation system.

## Overview

Before flight, three basic IMU calibrations are performed:

1. **Accelerometer calibration**
2. **Gyroscope calibration**
3. **Level calibration**

All measurements should first be converted from the **sensor frame to the quadcopter body frame**.

The body frame is defined as:

- **X → Roll axis**
- **Y → Pitch axis**
- **Z → Yaw axis**

The calibration process is therefore:

$$
\boxed{
\text{Sensor Frame}
\rightarrow
\text{Body Frame}
\rightarrow
\text{Accelerometer, Gyroscope and Level Calibration}
}
$$

## Accelerometer Calibration

Accelerometer calibration estimates sensor errors and determines a transformation that converts raw accelerometer measurements into corrected acceleration.

### Calibration Model

A general accelerometer calibration model is:

$$
\boxed{
\mathbf{a}_{corr}
=
\mathbf{T}
\left(
\mathbf{a}_{raw}-\mathbf{b}
\right)
}
$$

where:

- $\mathbf{a}_{raw}$ — raw accelerometer measurement
- $\mathbf{b}$ — accelerometer bias/offset vector
- $\mathbf{T}$ — $3\times3$ calibration matrix
- $\mathbf{a}_{corr}$ — corrected acceleration

The bias vector is:

$$
\mathbf{b}
=
\begin{bmatrix}
b_x\\
b_y\\
b_z
\end{bmatrix}
$$

and the calibration matrix is:

$$
\mathbf{T}
=
\begin{bmatrix}
T_{xx} & T_{xy} & T_{xz}\\
T_{yx} & T_{yy} & T_{yz}\\
T_{zx} & T_{zy} & T_{zz}
\end{bmatrix}
$$

The diagonal terms primarily account for **scale-factor errors**, while the off-diagonal terms can account for **axis misalignment and cross-axis sensitivity**.

### Methodology

Unlike the six-position method, multi-position calibration does not require the accelerometer to be placed in exactly known orientations.

The accelerometer is placed in many different **stationary and arbitrary orientations**. For every orientation, the direction of gravity may be different, but its magnitude is always known:

$$
\boxed{
\left\|
\mathbf{a}_{true}
\right\|
=
g
}
$$

where:

$$
g\approx9.81\ \mathrm{m/s^2}
$$

For each orientation, multiple samples are collected and averaged to reduce measurement noise.

#### 1. Collect Measurements

Place the stationary accelerometer in different arbitrary orientations and record the average raw acceleration:

$$
\mathbf{a}_{raw,i}
=
\begin{bmatrix}
a_{xi}\\
a_{yi}\\
a_{zi}
\end{bmatrix}
$$

for:

$$
i=1,\ldots,N
$$

**The orientations do not need to be exactly aligned with the X, Y, or Z axes.**

For example, a slightly tilted position may produce:

$$
\mathbf{a}_{raw}
=
\begin{bmatrix}
9.77\\
0\\
0.85
\end{bmatrix}
$$

This is valid because:

$$
\sqrt{9.77^2+0.85^2}
\approx
9.81
$$

The non-zero Z component is caused by the orientation of the accelerometer relative to gravity, not necessarily by sensor error.

#### 2. Validate Measurements

A measurement is accepted only when the accelerometer is sufficiently stationary and the measured acceleration magnitude is close to gravity.

The acceleration magnitude is calculated as:

$$
a_{mag}
=
\left\|
\mathbf{a}_{raw}
\right\|
$$

A practical validity condition is:

$$
\boxed{
9.7<a_{mag}<9.9\ \mathrm{m/s^2}
}
$$

In addition, the acceleration must remain stable over the sampling window:

$$
\boxed{
\sigma(a_{mag})<\epsilon_{\sigma}
}
$$

where:

- $\sigma(a_{mag})$ — standard deviation of the acceleration magnitude over the sampling window
- $\epsilon_{\sigma}$ — selected stability threshold

Only measurements satisfying both conditions are used for calibration.

#### 3. Define the Calibration Constraint

For every valid stationary measurement, the corrected acceleration should have a magnitude equal to gravity:

$$
\boxed{
\left\|
\mathbf{T}
\left(
\mathbf{a}_{raw,i}-\mathbf{b}
\right)
\right\|
\approx
g
}
$$

Therefore, define the calibration error for each measurement as:

$$
e_i
=
\left\|
\mathbf{T}
\left(
\mathbf{a}_{raw,i}-\mathbf{b}
\right)
\right\|
-g
$$

The objective is to make these errors as small as possible for all valid measurements.

#### 4. Least-Squares Estimation

The calibration parameters $\mathbf{T}$ and $\mathbf{b}$ are estimated by minimizing the total squared error:

$$
\boxed{
\min_{\mathbf{T},\mathbf{b}}
\sum_{i=1}^{N}e_i^2
}
$$

or equivalently:

$$
\boxed{
\min_{\mathbf{T},\mathbf{b}}
\sum_{i=1}^{N}
\left(
\left\|
\mathbf{T}
\left(
\mathbf{a}_{raw,i}-\mathbf{b}
\right)
\right\|
-g
\right)^2
}
$$

The resulting $\mathbf{b}$ and $\mathbf{T}$ are the calibration parameters that best fit all collected measurements.

#### 5. Apply Calibration

Once $\mathbf{b}$ and $\mathbf{T}$ have been determined, every subsequent raw measurement is corrected using:

$$
\boxed{
\mathbf{a}_{corr}
=
\mathbf{T}
\left(
\mathbf{a}_{raw}-\mathbf{b}
\right)
}
$$

For any stationary orientation, the corrected acceleration should satisfy:

$$
\boxed{
\left\|
\mathbf{a}_{corr}
\right\|
\approx
g
}
$$

The advantage of multi-position calibration is that small positioning errors and measurement noise are distributed across many measurements rather than being directly treated as calibration errors.

## Gyroscope Calibration

Gyroscope calibration estimates the sensor's **zero-rate bias** and determines the correction required to convert raw angular-rate measurements into corrected angular velocity.

### Calibration Model

The gyroscope measurement can be modeled as:

$$
\boxed{
\boldsymbol{\omega}_{corr}
=
\boldsymbol{\omega}_{raw}
-
\mathbf{b}_g
}
$$

where:

- $\boldsymbol{\omega}_{raw}$ — raw gyroscope measurement
- $\mathbf{b}_g$ — gyroscope bias (zero-rate offset)
- $\boldsymbol{\omega}_{corr}$ — corrected angular velocity

### Methodology

Gyroscope calibration is performed while the IMU is **completely stationary**, preferably in the level position.

When stationary, the true angular velocity is zero:

$$
\boxed{
\boldsymbol{\omega}_{true}
=
\begin{bmatrix}
0\\
0\\
0
\end{bmatrix}
}
$$

Therefore, the measured output during this condition primarily represents the gyroscope's bias and measurement noise.

#### 1. Collect Measurements

Keep the IMU completely stationary, preferably in the **level position**, and collect multiple gyroscope samples:

$$
\boldsymbol{\omega}_{raw,i}
=
\begin{bmatrix}
\omega_{xi}\\
\omega_{yi}\\
\omega_{zi}
\end{bmatrix}
$$

for:

$$
i=1,\ldots,N
$$

The samples are averaged to reduce random measurement noise.

#### 2. Estimate Gyroscope Bias

The zero-rate bias is estimated from the mean of the stationary measurements:

$$
\boxed{
\mathbf{b}_g
=
\frac{1}{N}
\sum_{i=1}^{N}
\boldsymbol{\omega}_{raw,i}
}
$$

For an ideal stationary gyroscope:

$$
\mathbf{b}_g
=
\begin{bmatrix}
0\\
0\\
0
\end{bmatrix}
$$

Any non-zero average represents the gyroscope's zero-rate offset.

#### 3. Validate Measurements

The IMU must remain stationary during calibration.

After removing the estimated bias, the residual angular velocity is:

$$
\boldsymbol{\omega}_{res,i}
=
\boldsymbol{\omega}_{raw,i}
-
\mathbf{b}_g
$$

The residual should satisfy:

$$
\boxed{
\left\|
\boldsymbol{\omega}_{res,i}
\right\|
<
\epsilon_{\omega}
}
$$

where $\epsilon_{\omega}$ is the maximum allowed residual angular-rate threshold.

Only stable measurements are used for calibration.

#### 4. Apply Calibration

Once the gyroscope bias has been determined, every subsequent raw measurement is corrected using:

$$
\boxed{
\boldsymbol{\omega}_{corr}
=
\boldsymbol{\omega}_{raw}
-
\mathbf{b}_g
}
$$

For a stationary gyroscope:

$$
\boxed{
\boldsymbol{\omega}_{corr}
\approx
\begin{bmatrix}
0\\
0\\
0
\end{bmatrix}
}
$$

The corrected angular velocity can then be integrated and used by the attitude estimator.

## Level Calibration

Keep the quadcopter stationary in the desired **level position** and collect multiple **calibrated accelerometer** samples.

- The measurements are considered valid when all three axes remain sufficiently stable:

  $$
  \boxed{
  \sigma_{a_x}<\epsilon_a,\qquad
  \sigma_{a_y}<\epsilon_a,\qquad
  \sigma_{a_z}<\epsilon_a
  }
  $$

  where $\epsilon_a=0.1\ \mathrm{m/s^2}$ is the selected accelerometer stability threshold.

- Average the valid samples:

  $$
  \mathbf{a}_{level}
  =
  \frac{1}{N}
  \sum_{i=1}^{N}
  \mathbf{a}_{corr,i}
  $$

- Calculate roll and pitch:
  $$
  \phi_{offset}
  =
  \operatorname{atan2}(a_y,a_z)
  $$

  $$
  \theta_{offset}
  =
  \operatorname{atan2}
  \left(
  -a_x,
  \sqrt{a_y^2+a_z^2}
  \right)
  $$

- During normal operation, compensate for the level offset:

  $$
  \boxed{
  \phi_{corr}
  =
  \phi-\phi_{offset}
  , \qquad
  \theta_{corr}
  =
  \theta-\theta_{offset}
  }
  $$

- After calibration, a physically level quadcopter should give:

  $$
  \boxed{
  \phi_{corr}\approx0^\circ,\qquad
  \theta_{corr}\approx0^\circ
  }
  $$

## Related Links

### External

- [PX4-Autopilot | Accelerometer Calibration](https://github.com/PX4/PX4-Autopilot/blob/main/src/modules/commander/accelerometer_calibration.cpp)
- [PX4-Autopilot | Gyroscope Calibration](https://github.com/PX4/PX4-Autopilot/blob/main/src/modules/commander/gyro_calibration.cpp)