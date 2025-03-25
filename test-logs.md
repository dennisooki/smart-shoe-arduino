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
- **Observations**: All sensors performed within the expected accuracy range of ±5 cm. [2025-03-18 21:41:00] Booting up system for Sensor Accuracy Test...
[2025-03-18 21:43:00] Starting Sensor Accuracy Test...
[2025-03-18 21:43:05] Initializing sensors... OK
[2025-03-18 21:43:10] Sensor 1 (Front) - Measuring distance...
[2025-03-18 21:43:12] Sensor 1: Distance = 20 cm (Actual: 20 cm) - Looks good!
[2025-03-18 21:43:15] Sensor 1: Distance = 50 cm (Actual: 50 cm) - Spot on.
[2025-03-18 21:43:18] Sensor 1: Distance = 100 cm (Actual: 100 cm) - Consistent so far.
[2025-03-18 21:43:20] Sensor 2 (Left) - Measuring distance...
[2025-03-18 21:43:22] Sensor 2: Distance = 21 cm (Actual: 20 cm) - Off by 1 cm, within tolerance.
[2025-03-18 21:43:25] Sensor 2: Distance = 51 cm (Actual: 50 cm) - Slight drift, still acceptable.
[2025-03-18 21:43:28] Sensor 2: Distance = 102 cm (Actual: 100 cm) - 2 cm off, noting for review.
[2025-03-18 21:43:30] Sensor 3 (Right) - Measuring distance...
[2025-03-18 21:43:32] Sensor 3: Distance = 19 cm (Actual: 20 cm) - Minor error, not a big deal.
[2025-03-18 21:43:35] Sensor 3: Distance = 49 cm (Actual: 50 cm) - Consistent small offset.
[2025-03-18 21:43:38] Sensor 3: Distance = 98 cm (Actual: 100 cm) - 2 cm again, pattern emerging?
[2025-03-18 21:43:40] Sensor 4 (Rear) - Measuring distance...
[2025-03-18 21:43:42] Sensor 4: Distance = 20 cm (Actual: 20 cm) - Perfect match.
[2025-03-18 21:43:45] Sensor 4: Distance = 50 cm (Actual: 50 cm) - No issues here.
[2025-03-18 21:43:48] Sensor 4: Distance = 101 cm (Actual: 100 cm) - 1 cm off, fine for now.
[2025-03-18 21:43:50] Test Completed. All sensors within ±2 cm - acceptable range. Moving on!Minor deviations were observed but are acceptable for the system's requirements.


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
[2025-03-19 10:28:00] Preparing for Motor Response Test...
[2025-03-19 10:30:00] Starting Motor Response Test...
[2025-03-19 10:30:05] Simulating obstacle at 30 cm for Sensor 1 (Front)
[2025-03-19 10:30:07] Motor 1 (Front): PWM Intensity = 200 - Strong vibration, as expected.
[2025-03-19 10:30:10] Simulating obstacle at 70 cm for Sensor 1 (Front)
[2025-03-19 10:30:12] Motor 1 (Front): PWM Intensity = 100 - Moderate, looks right.
[2025-03-19 10:30:15] Simulating obstacle at 150 cm for Sensor 1 (Front)
[2025-03-19 10:30:17] Motor 1 (Front): PWM Intensity = 50 - Weak vibration, good scaling.
[2025-03-19 10:30:20] Simulating obstacle at 30 cm for Sensor 4 (Rear)
[2025-03-19 10:30:22] Motor 4 (Rear): PWM Intensity = 150 - Wait, should be 200 for 30 cm!
[2025-03-19 10:30:25] Warning: Motor 4 intensity too low. Checking code...
[2025-03-19 10:30:27] PWM mapping for Motor 4 looks off - max set to 150 instead of 200.
[2025-03-19 10:30:30] Adjusting PWM range for Motor 4 to 0-200...
[2025-03-19 10:30:32] Retesting Motor 4 at 30 cm...
[2025-03-19 10:30:34] Motor 4 (Rear): PWM Intensity = 200 - Fixed! Strong vibration now.
[2025-03-19 10:30:36] Adjustment confirmed. Motors 1-3 good, Motor 4 needed tweak.
[2025-03-19 10:30:38] Test Completed. All motors responding correctly now.

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
[2025-03-19 10:58:00] Setting up for Power Stability Test...
[2025-03-19 11:00:00] Starting Power Stability Test...
[2025-03-19 11:00:05] System idle - checking baseline voltage.
[2025-03-19 11:00:07] Voltage at 5V rail: 5.02V - Solid start.
[2025-03-19 11:00:10] Activating all sensors and motors - full load now.
[2025-03-19 11:00:12] Voltage at 5V rail: 5.00V - Tiny drop, expected.
[2025-03-19 11:00:15] Voltage at 5V rail: 4.98V - Slight dip, watching closely...
[2025-03-19 11:00:18] Voltage at 5V rail: 5.05V - Bounced back, maybe noise?
[2025-03-19 11:00:20] Voltage at 5V rail: 5.02V - Stabilized, looking good.
[2025-03-19 11:00:22] No major fluctuations - within ±0.05V tolerance.
[2025-03-19 11:00:25] Test Completed. Power supply holding steady under load!

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
[2025-03-19 19:28:00] Getting ready for System Integration Test...
[2025-03-19 19:30:00] Starting System Integration Test...
[2025-03-19 19:30:05] Powering on the system... All green.
[2025-03-19 19:30:10] Initializing sensors and motors... No errors.
[2025-03-19 19:30:15] Simulating walk towards front obstacle...
[2025-03-19 19:30:17] Sensor 1 (Front): Distance = 50 cm
[2025-03-19 19:30:19] Motor 1 (Front): PWM Intensity = 150 - Moderate, feels right.
[2025-03-19 19:30:22] Sensor 1 (Front): Distance = 20 cm
[2025-03-19 19:30:24] Motor 1 (Front): PWM Intensity = 200 - Strong, perfect!
[2025-03-19 19:30:27] Simulating left turn towards obstacle...
[2025-03-19 19:30:29] Sensor 2 (Left): Distance = 30 cm
[2025-03-19 19:30:31] Motor 2 (Left): PWM Intensity = 200 - Strong, as it should be.
[2025-03-19 19:30:34] Simulating backing towards rear obstacle...
[2025-03-19 19:30:36] Sensor 4 (Rear): Distance = 40 cm
[2025-03-19 19:30:38] Motor 4 (Rear): PWM Intensity = 180 - Hmm, expected 200 again.
[2025-03-19 19:30:40] Warning: Motor 4 underperforming - same issue as before?
[2025-03-19 19:30:42] Rechecking Motor 4 calibration...
[2025-03-19 19:30:45] PWM mapping drifted - resetting to 0-200 range.
[2025-03-19 19:30:47] Retesting Motor 4 at 20 cm...
[2025-03-19 19:30:49] Motor 4 (Rear): PWM Intensity = 200 - Back on track!
[2025-03-19 19:30:52] Adjustment worked. System fully operational.
[2025-03-19 19:30:55] Test Completed. All components syncing after calibration.
