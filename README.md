# smart_phone's_fingerprint_sensor
int value1;
#define relay 9
const int buzzer = 7; 
void setup()
{
    Serial.begin(9600);
    pinMode(relay, OUTPUT);
    pinMode(buzzer, OUTPUT); 
    digitalWrite(relay, LOW);
}
void loop()
{
  Serial.print("Reading");
  while(Serial.available()==0);
  value1 = Serial.read();
  Serial.print(value1);
  if (value1==1)
  { 
    Serial.print("Unlocking");
    digitalWrite(relay, LOW);
    digitalWrite(buzzer, HIGH); 
    delay(1000);        
    digitalWrite(buzzer, LOW); 
  }
  if (value1==0)
  {
      digitalWrite(relay, HIGH);
      Serial.print("Locking");
  }
}
