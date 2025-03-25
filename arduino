#define FRONT_TRIG 2    // Front sensor trig pin
#define FRONT_ECHO 3    // Front sensor echo pin
#define LEFT_TRIG 4     // Left sensor trig pin
#define LEFT_ECHO 5     // Left sensor echo pin
#define RIGHT_TRIG 6    // Right sensor trig pin
#define RIGHT_ECHO 7    // Right sensor echo pin
#define REAR_TRIG 8     // Rear sensor trig pin
#define REAR_ECHO 9     // Rear sensor echo pin

#define FRONT_MOTOR 10  // Front motor PWM pin
#define LEFT_MOTOR 11   // Left motor PWM pin
#define RIGHT_MOTOR 12  // Right motor PWM pin
#define REAR_MOTOR 13   // Rear motor PWM pin

long duration, distance;

void setup() {
  Serial.begin(9600);
  // Initialize sensor pins
  pinMode(FRONT_TRIG, OUTPUT); pinMode(FRONT_ECHO, INPUT);
  pinMode(LEFT_TRIG, OUTPUT);  pinMode(LEFT_ECHO, INPUT);
  pinMode(RIGHT_TRIG, OUTPUT); pinMode(RIGHT_ECHO, INPUT);
  pinMode(REAR_TRIG, OUTPUT);  pinMode(REAR_ECHO, INPUT);
  // Initialize motor pins
  pinMode(FRONT_MOTOR, OUTPUT);
  pinMode(LEFT_MOTOR, OUTPUT);
  pinMode(RIGHT_MOTOR, OUTPUT);
  pinMode(REAR_MOTOR, OUTPUT);
}

long readSensor(int trigPin, int echoPin) {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  return duration / 58.2;  // Distance in cm
}

void activateMotor(int motorPin, long distance) {
  if (distance < 100) {  // Within 1m
    int intensity = map(distance, 0, 100, 255, 50);  // Stronger for closer obstacles
    analogWrite(motorPin, intensity);
    delay(100);
    analogWrite(motorPin, 0);
  }
}

void loop() {
  // Read distances from all sensors
  long frontDist = readSensor(FRONT_TRIG, FRONT_ECHO);
  long leftDist = readSensor(LEFT_TRIG, LEFT_ECHO);
  long rightDist = readSensor(RIGHT_TRIG, RIGHT_ECHO);
  long rearDist = readSensor(REAR_TRIG, REAR_ECHO);

  // Print distances for debugging
  Serial.print("Front: "); Serial.println(frontDist);
  Serial.print("Left: "); Serial.println(leftDist);
  Serial.print("Right: "); Serial.println(rightDist);
  Serial.print("Rear: "); Serial.println(rearDist);

  // Activate motors based on distances
  activateMotor(FRONT_MOTOR, frontDist);
  activateMotor(LEFT_MOTOR, leftDist);
  activateMotor(RIGHT_MOTOR, rightDist);
  activateMotor(REAR_MOTOR, rearDist);

  delay(50);  // Small delay to prevent overlap
}
