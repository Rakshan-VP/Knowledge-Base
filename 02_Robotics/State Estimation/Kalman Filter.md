#type/concept #domain/robotics #status/learning #scope/intermediate
> [!abstract] Summary
> A Kalman filter estimates the true state of a system by combining what the **model predicts** with what the **sensor measures**. It automatically gives more weight to whichever is considered more reliable, making it useful for reducing sensor noise and improving state estimates.

## Introduction
The Kalman filter is a smart way to figure out where a moving object really is, even when sensors are noisy and inaccurate. Before **1960**, older math methods had to store and re-calculate every single past measurement, which melted the slow computers of the time. A mathematician named **Rudolf Kálmán** solved this by making the filter need only the current sensor reading and the most recent guess, using almost **no memory**. NASA engineer **Stanley Schmidt** realized this was the breakthrough they needed to steer spacecraft through deep space. In **1969**, it famously ran inside the tiny **Apollo 11** navigation computer, safely guiding astronauts to land on the Moon.

## Concept

A Kalman filter estimates the current system state by combining a **model-based prediction** with a **measurement**.

### System Representation

The system is represented by the discrete-time state-space model:

$$  
\boxed{  
\begin{aligned}  
x_k &= A x_{k-1} + B u_k + w_k \\  
z_k &= C x_k + v_k  
\end{aligned}  
}  
$$

where:

|Symbol|Meaning|
|---|---|
|$x_k$|True state at time $k$|
|$A$|State transition matrix|
|$B$|Control-input matrix|
|$u_k$|Known input/control|
|$w_k$|Process noise|
|$z_k$|Measurement|
|$C$|Measurement matrix|
|$v_k$|Measurement noise|

The process and measurement noises are assumed to be zero-mean [[Gaussian Distribution|Gaussian]]:

$$  
\boxed{  
w_k \sim \mathcal{N}(0,Q)  
\qquad  
v_k \sim \mathcal{N}(0,R)  
}  
$$
### Covariance Matrices

- **$P$ — Estimate Error Covariance**
    
    - $P$ represents the uncertainty in the estimated state.
        
    - A large $P$ means the estimate is uncertain.
        
    - A small $P$ means the estimate is more reliable.
        
- **$Q$ — Process Noise Covariance**
    
    - $Q$ represents uncertainty in the system model.
        
    - Large $Q$ → the model is considered less reliable.
        
    - Small $Q$ → the model is considered more reliable.
        
- **$R$ — Measurement Noise Covariance**
    
    - $R$ represents uncertainty in the sensor measurement.
        
    - Large $R$ → the measurement is considered less reliable.
        
    - Small $R$ → the measurement is considered more reliable.
        

The Kalman filter therefore keeps track of both:

- the estimated state $\hat{x}$
    
- the uncertainty of that estimate $P$
    

### Prediction

The **prediction step** uses the previous estimate and the system model to predict the current state.

- **Predicted State**
$$  
\boxed{  
\hat{x}_k^- = A\hat{x}_{k-1} + Bu_k  
}  
$$
The superscript $-$ denotes the **a priori estimate** — the estimate before using the current measurement.

- **Predicted Error Covariance**
$$  
\boxed{  
P_k^- = AP_{k-1}A^T + Q  
}  
$$
The process noise covariance $Q$ increases the predicted uncertainty.

### Update

The **update step** uses the current measurement to correct the predicted state.

- **Kalman Gain**
$$  
\boxed{  
K_k =  
P_k^-C^T  
\left(CP_k^-C^T + R\right)^{-1}  
}  
$$
The Kalman gain determines how much the measurement should influence the predicted state.

- **Innovation**
The difference between the actual measurement and the predicted measurement is:
$$  
z_k - C\hat{x}_k^-  
$$
This is called the **innovation** or **measurement residual**.

- **Updated State**
$$  
\boxed{  
\hat{x}_k =  
\hat{x}_k^- +  
K_k\left(z_k-C\hat{x}_k^-\right)  
}  
$$
- **Updated Error Covariance**
$$  
\boxed{  
P_k = (I-K_kC)P_k^-  
}  
$$
After the update, $\hat{x}_k$ and $P_k$ become the starting point for the next iteration.

> [!note] Kalman Gain — Two Limiting Cases
> The Kalman gain determines the balance between the **measurement** and **prediction**.
>
> **Measurement very reliable:**  
> $R \rightarrow 0 \Rightarrow K_k \rightarrow C^{-1}$  
> For $C=I$: $K_k \rightarrow I$, so $\hat{x}_k \rightarrow z_k$.
>
> **Prediction very reliable:**  
> $P_k^- \rightarrow 0 \Rightarrow K_k \rightarrow 0$, so $\hat{x}_k \rightarrow \hat{x}_k^-$.

The Kalman filter continuously balances the uncertainty of the **model prediction** against the uncertainty of the **measurement**.

### Advantages
- **Optimal estimation** under linear, Gaussian assumptions.
- **Combines model and measurement** based on their uncertainties.
- **Reduces measurement noise** while preserving useful dynamics.
- **Provides uncertainty** through the error covariance $P$.
- **Computationally efficient** and suitable for real-time systems.
- **Adaptive weighting** through the Kalman gain $K$.

### Limitations
- **Requires an accurate system model** ($A$, $B$, and $C$).
- Assumes **linear system dynamics**; nonlinear systems require variants such as EKF or UKF.
- Assumes **Gaussian, zero-mean noise** for standard optimality guarantees.
- Performance depends strongly on choosing appropriate **$Q$ and $R$**.
- **Bias and unmodeled disturbances** can cause persistent estimation errors unless explicitly modeled.
- Poorly chosen $Q$, $R$, or initial $P$ can cause **slow convergence or noisy estimates**.
- Requires **matrix operations/inversion**, which can become expensive for high-dimensional systems.
## Related Links
### Examples
- [[Gaussian Distribution]]
- [[Kalman Filter]]
### Notes
- [[Gaussian Distribution]]
## References
- [Why Use Kalman Filters? | Understanding Kalman Filters, Part 1](https://www.youtube.com/watch?v=mwn8xhgNpFY)
- [Optimal State Estimator Algorithm | Understanding Kalman Filters, Part 4](https://www.youtube.com/watch?v=VFXf1lIZ3p8)
