# ph sensor
// Define the pin where the pH sensor is connected
const int pHpin = A0;

// Calibration values
float calibrationValue = 21.34; // Adjust based on your specific sensor

void setup() {
  Serial.begin(9600); // Start the serial communication
  pinMode(pHpin, INPUT);
}

void loop() {
  int sensorValue = analogRead(pHpin); // Read the analog value from the sensor
  float voltage = sensorValue * (5.0 / 1023.0); // Convert the analog value to voltage
  float pHValue = 3.5 * voltage + calibrationValue; // Calculate the pH value

  Serial.print("pH Value: ");
  Serial.println(pHValue); // Print the pH value to the Serial Monitor

  delay(1000); // Wait for a second before taking another reading
}
