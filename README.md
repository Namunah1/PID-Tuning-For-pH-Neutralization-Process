# PID Tuning for pH Neutralization Process

## 📘 Course

**Process Dynamics and Control**

## 👥 Group Members

* Ashish Donth (230008011)
* Kumar Prince (230008019)

---

## 📌 Project Overview

pH control is one of the most challenging control problems in chemical process industries due to its **highly nonlinear behavior** and **slow process dynamics**.

This project focuses on:

* Designing and tuning a **PID controller**
* Regulating a **pH neutralization process**
* Maintaining a setpoint of **pH = 8**
* Handling **disturbances in feed concentration and flow rate**
* Comparing performance with and without **Internal Model Control (IMC)**

The goal is to achieve **stable, robust, and disturbance-resistant pH control** under realistic industrial conditions.

---

## ⚙️ Process Description

The pH neutralization process involves mixing acidic/basic streams with a neutralizing agent to reach a desired pH value.

### 🔹 Process Characteristics

* First-order dynamics
* Transport delay
* Measurement noise (realistic pH probe behavior)
* Slow response due to mixing and reaction kinetics

### 🔹 Transfer Function

[
G(s) = \frac{14s + 25}{1478.26s + 1}
]

**Where:**

* **25** → Steady-state gain
* **Zero at s = -1.79** → Lead behavior
* **τ = 1478.26 s** → Large time constant (slow process)
* Transport delay → Accounts for residence time and mixing lag

---

## 🎯 Controller Design

### Step 1: Ziegler-Nichols Closed-Loop Tuning

Estimated parameters:

* Ultimate Gain → ( K_u ≈ 48 )
* Oscillation Period → ( P_u ≈ 100 ) s

Using ZN tuning formulas:

| Parameter | Calculated | Final Adjusted |
| --------- | ---------- | -------------- |
| Kp        | 28.8 ≈ 29  | 29             |
| Ki        | 0.58       | 2              |
| Kd        | 360        | 2              |

> Derivative gain was significantly reduced due to measurement noise sensitivity.

### 🔹 Baseline PID Parameters

```
Kp = 29
Ki = 2
Kd = 2
```

---

## 📊 Results & Performance Analysis

The system was tested under multiple scenarios:

### 1️⃣ Without IMC

* Sharp initial transient
* Fast settling
* Small overshoot

### 2️⃣ With IMC

* Smooth response
* Minimal overshoot
* Improved robustness

### 3️⃣ Concentration Disturbance

* Increased derivative action required
* Reduced integral gain to prevent windup

### 4️⃣ Flow Rate Disturbance (400% increase)

* Required strong derivative action
* Moderate proportional gain

### 5️⃣ Combined Disturbances

* Balanced tuning for robustness

---

## 📈 Performance Comparison

| Scenario      | Kp | Ki  | Kd | Key Feature                       |
| ------------- | -- | --- | -- | --------------------------------- |
| Without IMC   | 29 | 2   | 2  | Fast settling                     |
| With IMC      | 29 | 2   | 2  | Smooth response                   |
| Concentration | 18 | 0.5 | 10 | High damping                      |
| Flow Rate     | 17 | 0.5 | 11 | Strong disturbance rejection      |
| Combined      | 24 | 0.5 | 4  | Robust multi-disturbance handling |

---

## 🔎 Key Observations

* IMC significantly improves transient performance.
* Concentration disturbances require high derivative gain.
* Flow disturbances demand strong derivative control.
* Combined disturbances require compromise tuning.
* Transport delay and noise increase control complexity.

---

## 🏁 Conclusion

This project successfully demonstrates:

* Practical PID tuning for nonlinear pH processes
* Effectiveness of Ziegler-Nichols for initial parameter estimation
* Importance of derivative action for disturbance rejection
* Benefits of IMC for smoother control response

### 🚀 Future Scope

* Adaptive PID tuning
* Gain scheduling
* Model Predictive Control (MPC)
* Nonlinear control strategies

---

## 🛠️ Tools Used

* MATLAB / Simulink (for modeling and simulation)
* Control System Toolbox

---

## 📂 Repository Structure

```
├── Report.pdf
├── Simulation Files
├── Plots
└── README.md
```

---

## 📌 How to Use

1. Clone the repository
2. Open simulation files in MATLAB/Simulink
3. Run scenarios for different disturbance conditions
4. Compare responses with and without IMC

---
