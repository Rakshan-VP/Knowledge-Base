## IMU Roll Estimation — State-Space Model

I am using a 2-state model:

$$
\mathbf{x}=
\begin{bmatrix}
\phi\\
b_g
\end{bmatrix}
$$

where:

- $\phi$ = roll angle
- $b_g$ = gyroscope bias

### Continuous-Time Model

The gyroscope measurement is

$$
\omega_m=\dot{\phi}+b_g+w_g
$$

where $w_g$ represents random gyroscope measurement noise.

The gyro bias is assumed to vary slowly:

$$
\dot{b}_g=w_b
$$

Therefore, the continuous-time state-space model is

$$
\boxed{
\dot{\mathbf{x}}
=
\underbrace{
\begin{bmatrix}
0 & -1\\
0 & 0
\end{bmatrix}}_{\mathbf{A}}
\mathbf{x}
+
\underbrace{
\begin{bmatrix}
1\\
0
\end{bmatrix}}_{\mathbf{B}}
\omega_m
+
\mathbf{w}
}
$$

where

$$
\mathbf{w}=
\begin{bmatrix}
-w_g\\
w_b
\end{bmatrix}
$$

is the process noise.

The accelerometer provides the roll measurement:

$$
\phi_{acc}=\operatorname{atan2}(a_y,a_z)
$$

After calibration of the accelerometer roll offset:

$$
\boxed{
z=\phi_{acc}-\phi_{offset}
}
$$

The measurement equation is

$$
\boxed{
z=
\underbrace{
\begin{bmatrix}
1 & 0
\end{bmatrix}}_{\mathbf{C}}
\mathbf{x}
+v
}
$$

where $v$ represents accelerometer measurement noise.

---

### Discrete-Time Model

For a sampling time $\Delta t$:

$$
\boxed{
\mathbf{x}_k
=
\mathbf{A}_d\mathbf{x}_{k-1}
+
\mathbf{B}_d\omega_{m,k}
+
\mathbf{w}_k
}
$$

where

$$
\boxed{
\mathbf{A}_d=
\begin{bmatrix}
1 & -\Delta t\\
0 & 1
\end{bmatrix}
}
$$

and

$$
\boxed{
\mathbf{B}_d=
\begin{bmatrix}
\Delta t\\
0
\end{bmatrix}
}
$$

The discrete measurement equation is

$$
\boxed{
z_k=\mathbf{C}\mathbf{x}_k+v_k
}
$$

with

$$
\boxed{
\mathbf{C}=
\begin{bmatrix}
1 & 0
\end{bmatrix}.
}
$$

### Bias Handling

- **Accelerometer bias:** Calibrate the accelerometer roll offset beforehand and subtract it from $\phi_{acc}$.
- **Gyroscope bias:** Include $b_g$ as a state and estimate it **online** using the Kalman filter.

Thus, the Kalman filter estimates:

$$
\boxed{
\mathbf{x}_k=
\begin{bmatrix}
\hat{\phi}_k\\
\hat{b}_{g,k}
\end{bmatrix}
}
$$