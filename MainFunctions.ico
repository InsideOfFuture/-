int val;
int MOTOR = 3;

long readUltrasonicDistance(int triggerPin, int echoPin)
{
	pinMode(triggerPin, OUTPUT);  // Clear the trigger
	digitalWrite(triggerPin, LOW);
	delayMicroseconds(2);
	// Sets the trigger pin to HIGH state for 10 microseconds
	digitalWrite(triggerPin, HIGH);
	delayMicroseconds(10);
	digitalWrite(triggerPin, LOW);
	pinMode(echoPin, INPUT);
	// Reads the echo pin, and returns
	// the sound wave travel time in microseconds
	return pulseIn(echoPin, HIGH);
}
void setup()
{
  Serial.begin(9600);
  pinMode(MOTOR, OUTPUT);
  pinMode(5, OUTPUT);
}
void loop()
{
  int forwarddistance = readUltrasonicDistance(4,2);
  int backdistance = readUltrasonicDistance(6,7);
  delay(500);
  if (Serial.available())
  {
    val = Serial.read();
    // При символе "1" включаем светодиод
    if (val == '1')
    {
        while (val == '1') {
          if ((0.0344/2 *forwarddistance <= 33) or (0.0344/2 *backdistance <= 33)) {
    digitalWrite(5,HIGH);
    analogWrite(MOTOR,0);
    delay(500);
    }
    else{
    digitalWrite(5,LOW);
    analogWrite(MOTOR,3000);
    }
        }
    }
    // При символе "0" выключаем светодиод
    if ( val == '0')
    {
      analogWrite(MOTOR, 0);
    }
  }



  
}
