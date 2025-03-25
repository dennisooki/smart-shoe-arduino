### **Test Logs for Smart Shoe Project**

#### **Test 1: Sensor Accuracy**

- **Objective**: Verify that each HC-SR04 ultrasonic sensor accurately measures distances to obstacles.
- **Procedure**:
  1. Place an obstacle at known distances (20 cm, 50 cm, and 100 cm) from each sensor, one at a time.
  2. Record the distance measured by the sensor for each placement.
  3. Repeat for all four sensors.
- **Expected Results**: The measured distance should be within ±5 cm of the actual distance for each sensor.
- **Actual Results**:
  - **Sensor 1 (Front)**: 
    - 20 cm (actual: 20 cm), 50 cm (actual: 50 cm), 100 cm (actual: 100 cm)
  - **Sensor 2 (Left)**: 
    - 21 cm (actual: 20 cm), 51 cm (actual: 50 cm), 102 cm (actual: 100 cm)
  - **Sensor 3 (Right)**: 
    - 19 cm (actual: 20 cm), 49 cm (actual: 50 cm), 98 cm (actual: 100 cm)
  - **Sensor 4 (Rear)**: 
    - 20 cm (actual: 20 cm), 50 cm (actual: 50 cm), 101 cm (actual: 100 cm)
- **Observations**: All sensors performed within the expected accuracy range of ±5 cm. Minor deviations were observed but are acceptable for the system's requirements.

---

#### **Test 2: Motor Response**

- **Objective**: Ensure that each vibration motor responds correctly to sensor inputs based on obstacle proximity.
- **Procedure**:
  1. Simulate obstacle detection by manually triggering each sensor at different distances (e.g., 30 cm, 70 cm, 150 cm).
  2. Observe the corresponding motor's vibration intensity for each simulated distance.
  3. Verify that the motor vibrates strongly for close obstacles and weakly for distant ones.
- **Expected Results**: Motors should vibrate with intensity inversely proportional to the distance of the obstacle (stronger for closer obstacles, weaker for farther ones).
- **Actual Results**:
  - **Motor 1 (Front)**: Vibrated strongly at 30 cm, moderately at 70 cm, and weakly at 150 cm.
  - **Motor 2 (Left)**: Similar behavior to Motor 1.
  - **Motor 3 (Right)**: Vibrated as expected across all distances.
  - **Motor 4 (Rear)**: Vibrated, but the intensity was inconsistent, particularly at closer distances.
- **Observations**: Motors 1, 2, and 3 performed as expected. Motor 4's intensity was lower than anticipated for close obstacles, indicating a need for further calibration or adjustment in the PWM mapping.

---

#### **Test 3: Power Stability**

- **Objective**: Verify that the LM7805 voltage regulator provides a stable 5V output to the system during operation.
- **Procedure**:
  1. Measure the voltage at the 5V rail using a multimeter while the system is idle.
  2. Measure the voltage again while the system is actively detecting obstacles and vibrating motors.
  3. Monitor for any significant voltage fluctuations.
- **Expected Results**: The voltage should remain stable at 5V ±0.5V during both idle and operational states.
- **Actual Results**:
  - **Idle State**: 5.02V
  - **Operational State**: Voltage fluctuated between 4.98V and 5.05V
- **Observations**: The voltage remained stable within the acceptable range, ensuring reliable operation of the system. No significant drops or spikes were observed during testing.

---

#### **Test 4: System Integration**

- **Objective**: Test the entire system to ensure all components (sensors, motors, and power supply) work together seamlessly in a simulated real-world environment.
- **Procedure**:
  1. Power on the system and place it in a test environment with obstacles positioned in front, left, right, and rear directions.
  2. Simulate a user walking through the environment, approaching obstacles from different directions.
  3. Observe whether the corresponding motors provide accurate and timely haptic feedback based on obstacle proximity.
- **Expected Results**: The system should detect obstacles in all four directions and provide appropriate haptic feedback through the corresponding motors.
- **Actual Results**:
  - **Front Obstacle**: Front motor vibrated strongly when approaching the obstacle.
  - **Left Obstacle**: Left motor vibrated correctly as the obstacle was approached.
  - **Right Obstacle**: Right motor vibrated appropriately.
  - **Rear Obstacle**: Rear motor vibrated, but the intensity was lower than expected for close proximity.
- **Observations**: The system successfully detected obstacles in all directions. However, the rear motor's feedback was less intense than desired for close obstacles, suggesting a need for fine-tuning the vibration intensity mapping for that motor.

---
