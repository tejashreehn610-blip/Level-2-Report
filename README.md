# TASK 3 Introduction to MATLAB :
**Objective :** To gain foundational knowledge of MATLAB and Simulink.
**Learnings and Outcomes :**\
I have learnt the basics of MATLAB.
![IMAGE](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/e76826e524ae5ba391d4d6b7c7e0484e58a0d3c0/Screenshot%202026-10-09%20235100.png)\
![IMAGE](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/e76826e524ae5ba391d4d6b7c7e0484e58a0d3c0/Screenshot%202026-10-10%20000110.png)\
# TASK 4 Advanced PID Tuning :

---

## 1. Executive Summary & PID Fundamentals

A Proportional-Integral-Derivative (PID) controller is a control loop feedback mechanism widely used in industrial control systems and autonomous vehicles. It continuously calculates an error value as the difference between a desired setpoint r(t) and a measured process variable y(t), and applies a correction based on proportional, integral, and derivative terms.

---

## 2. Learnings from Video Resources (PID in Depth)

Based on reviewing the core PID resource playlist, the breakdown of each tuning parameter is as follows:

*   **Proportional (P):** 
    *   *Function:* Reacts directly to the current error.
    *   *Effect:* Reduces the rise time and steady-state error. However, setting P too high leads to aggressive oscillations, system overshoot, and instability.
*   **Integral (I):** 
    *   *Function:* Accumulates the error over time.
    *   *Effect:* Eliminates steady-state errors (such as persistent wind drift or imbalances). Too much I, however, causes slow oscillations, phase lag, and integrator windup.
*   **Derivative (D):** 
    *   *Function:* Predicts future error by evaluating the rate of change.
    *   *Effect:* Acts as a damper to smooth out system response, reduce overshoot, and improve transient stability. High $D$ values amplify high-frequency sensor noise.

---

## 3. UAV Mission Planner PID Configuration

Connecting a UAV flight controller to Mission Planner allows monitoring and modifying the stabilization loop parameters:

| Axis | Proportional (P) | Integral (I) | Derivative (D) | Description & Observations |
| :--- | :--- | :--- | :--- | :--- |
| **Roll** | 0.135 | 0.135 | 0.0036 | Manages lateral stabilization; reacts immediately to rolling disturbances. |
| **Pitch** | 0.135 | 0.135 | 0.0036 | Manages longitudinal tilt; mirrors Roll performance on symmetric frames. |
| **Yaw** | 0.200 | 0.020 | 0.0000 | Controls heading rotation; typically requires lower damping due to rotational inertia. |

---

## 4. Self-Balancing Car Implementation

A two-wheeled self-balancing robot was built to validate PID principles in hardware:

1. **Sensor Fusion:** An MPU6050 IMU combines accelerometer data (gravity reference) and gyroscope data (rotation rate) via a complementary filter to determine the precise tilt angle.
2. **Control Loop:** Operating at a consistent loop frequency (e.g., every 10 milliseconds), the microcontroller calculates the PID output based on the tilt angle error.
3. **Actuation:** The computed control output adjusts the PWM signals sent to the motor driver, driving the wheels forward or backward to counteract the falling motion and maintain balance.

---

## 5. Experimental Tuning Observations

Tuning the system iteratively using manual trial-and-error yielded the following practical behaviors:

*   **Tuning P Independently:** Setting I=0 and D=0 and raising $P$ caused the robot to rapidly twitch and oscillate back and forth across the balance point without stopping.
*   **Adding D Damping:** Introducing the D term successfully dampened the rapid oscillations, stabilizing the snapping movements and bringing the system to a smooth equilibrium.
*   **Adding I Correction:** Adding a small amount of I eliminated slight steady-state leaning biases caused by uneven weight distribution, whereas an excessive I value caused slow, growing oscillations.
# TASK 5 RULES IN THE RULE BOOK WRITTEN BY BLOOD :
**Objective :**
* Take an example of a previous Air Crash from [Wyngx](https://www.youtube.com/@_WyngX/videos) or any other source of your choice.
* Write a detailed report of the air crash investigation, the report should include:
  * Details of the flight, place, time, pilot details and an introductory paragraph about the accident which occurred /was about to occur including the losses occurred.
  * Explain in brief about the aircraft.
  * Using the Swiss Cheese Model analyze the key contributing factors (technical, human, environmental etc.) and also explain how each of these factors (layers of the Swiss Cheese) accelerated the accident when aligned together.
  * State the various theories and assumptions which took place during the investigation and also mention the reasons which led to the elimination/confirmation of these theories.
  * Reflect on what lessons were learned and how aviation standards changed post accident.

**Learnings and Outcomes :**\
I reported on the Crash of Air India flight 171, which crashed on the Ahmedabad Airport on June 12, 2025.\
[Click Here](https://github.com/tejashreehn610-blip/Aircrash-Report/blob/87ad5f9c15154d4f41930726e8e51594ae7e754f/AIR%20INDIA%20FLIGHT%20171%20CRASH%20REPORT%20(1).pdf) to view my Air Crash Investigation Report.\
The final official investigation report for AIT INDIA FLIGHT 171 is not yet been released.\
**References :** \
[AIR CRASH INVESTIGATION VIDEO](https://youtu.be/Hrdp50Dm_FE?si=FSHaGTcWtqf7elDO)\
# TASK 6 Flight Data Logging & Analysis :
**Objective :**\
 To explore the methodology behind air crash investigations and learn how aviation safety evolves from past incidents.\
1. Extract log files from a Pixhawk/APM flight controller.\
2. Analyze flight stability, GPS accuracy, battery performance using Mission Planner.\
3. Generate graphs for:\
Altitude vs time.
Throttle & Battery vs time consumption.
Velocity vs time\
**Learnings and Outcomes :**\
1.Crash Log :\
* Crash Auto Log:\
![image](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/8a811e412840c9c9a2f41a2eb41208f181b595d1/Screenshot%202026-10-08%20141753.png)\
* Altitude vs Time:\
![image](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/b6d486013a083e63f313a96759fb77d49b0014a6/Screenshot%202026-10-08%20142458.png)\
This graph shows that the altitude remains below zero throughout the log.\
The vehicle never gains positive altitude, indicating no successful takeoff.\
Small fluctuations suggest minor throttle inputs or sensor noise while staying on the ground.\
This behavior is consistent with a failed takeoff or crash shortly after arming.\
2.Simulator Log :\
* Simulator Auto Log
![image](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/0c541fc5efef816bff0b50af3fc8e3770afaa76d/Screenshot%202026-10-08%20143452.png)\
* Altitude vs Time:\
![image](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/80749024d1f887059cca4126b68d70107b6b7f37/Screenshot%202026-10-08%20143650.png)\
This graph shows the altitude used by the flight controller for control.
The altitude stays near 0 m initially, indicating the vehicle is on the ground, during STABILISE mode.
A sharp rise to about 150 m represents the takeoff and rapid climb phase, during AUTO mode.
Such a steep change is typical in simulator or auto-mission flights, where altitude is commanded quickly.\
* Throttle vs Time:\
![image](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/80749024d1f887059cca4126b68d70107b6b7f37/Screenshot%202026-10-08%20143829.png)\
This graph shows the actual throttle output commanded by the flight controller.
The throttle remains near 0 initially, indicating the vehicle is on the ground or disarmed.
A sharp rise to about 0.45–0.48 corresponds to takeoff and climb, where higher throttle is required.\
* Battery Consumption vs Time :\
![image](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/80749024d1f887059cca4126b68d70107b6b7f37/Screenshot%202026-10-08%20143956.png)\
This graph shows the total battery capacity consumed (in mAh) since arming.
The flat line at the start indicates no power draw while the vehicle is on the ground.
The sharp upward rise corresponds to takeoff and active flight, where current is being drawn continuously.
The final value (~1740 mAh) represents the total energy used during the flight.\
3. AMS Log :
* Auto Log :
![IMAGE](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/660ca2b41335676166c91d74c3de318bc2a80c04/Screenshot%202026-10-08%20145017.png)\
* Altitude vs Time
![IMAGE](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/660ca2b41335676166c91d74c3de318bc2a80c04/Screenshot%202026-10-08%20145123.png)\
A stable altitude curve indicates good vertical control and sensor reliability.\
![IMAGE](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/97ecbb2521b42e3c07434ec6e8ef33be95b2cf5d/WhatsApp%20Image%202026-10-11%20at%206.13.03%20PM.jpeg)\
 Consistent velocity indicates predictable flight dynamics.\
# TASK 7 Introduction to ROS 2 for UAVs :
**Objective :**
 To get started with the Robot Operating System (ROS) 2 ecosystem and understand its application in UAV communication through node-based architecture.
 **Learnings and Outcomes :**
 Document of every step of this task is below with screenshorts :
 ![image](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/b26b88c26c843f49a090bcdf24042c998232d75f/Screenshot%202026-10-11%20160247.png)Publisher code
![Image](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/7c6ac7624a36501955409f5e74791f7881948f17/Screenshot%202026-10-10%20181925.png)Publisher output
![input](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/70499f04c35a81aa3dd752c740e9e5d8386b4f8c/Screenshot%202026-10-11%20160317.png)setup code
![image](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/e8dced9368ebf5e4ca7c8eb5aad35206ecf047e0/Screenshot%202026-10-11%20160304.png)Suscriber code\
![image](https://raw.githubusercontent.com/tejashreehn610-blip/Level-2-Report/bc86cc8471f0b6a273408cc1924dafe70510fef4/Screenshot%202026-10-10%20184512.png)Suscriber output\
[click here](https://github.com/tejashreehn610-blip/ROS2.git) to view my R0S 2 documentation.\


