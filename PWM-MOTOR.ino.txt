// Pin definitions for HC-SR04 Ultrasonic Sensor
const int trigPin = 2;
const int echoPin = 3;

// Pin definitions for L293D Motor Driver
const int enablePin = 5; // PWM pin for speed control
const int motorPin1 = 4; // Control pin 1
const int motorPin2 = 7; // Control pin 2

const int stopDistance = 20; // Stopping threshold in cm

void setup() {
  Serial.begin(9600);

  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);

  pinMode(enablePin, OUTPUT);
  pinMode(motorPin1, OUTPUT);
  pinMode(motorPin2, OUTPUT);
}

void loop() {
  // 1. Measure distance
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  long duration = pulseIn(echoPin, HIGH);
  int distance = duration * 0.034 / 2;

  // 2. Motor Logic using PWM speed control
  if (distance > 0 && distance <= stopDistance) {
    // Obstacle detected close by! Stop motor completely.
    analogWrite(enablePin, 0); 
    digitalWrite(motorPin1, LOW);
    digitalWrite(motorPin2, LOW);
    
    Serial.print("OBSTACLE DETECTED! Distance: ");
    Serial.print(distance);
    Serial.println(" cm. Motor STOPPED.");
  } 
  else {
    // Path clear! Run motor forward at an active speed profile (PWM 180)
    analogWrite(enablePin, 180); 
    digitalWrite(motorPin1, HIGH); 
    digitalWrite(motorPin2, LOW);
    
    Serial.print("Path Clear. Distance: ");
    Serial.print(distance);
    Serial.println(" cm. Motor Running.");
  }

  delay(200); 
}