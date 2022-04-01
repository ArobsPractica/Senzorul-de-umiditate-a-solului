const int AirValue = 870;
const int WaterValue = 410;
int soilMoistureValue = 0;
int soilmoisturepercent = 0;
unsigned long timing;
unsigned long lastTime;
int timer = 1000;
void setup() {
  Serial.begin(9600);
}
void loop() {
  lastTime = millis();

if (lastTime - timing >= timer) 
{
  soilMoistureValue = analogRead(A0);  //introducem senzorul in pamant

  soilmoisturepercent = map(soilMoistureValue, AirValue, WaterValue, 0, 100);
  if (soilmoisturepercent >= 100)
  {
    Serial.println("100 %");
  }
  else if (soilmoisturepercent <= 0)
  {
    Serial.println("0 %");
  }
  else if (soilmoisturepercent > 0 && soilmoisturepercent < 100)
  {
    Serial.print(soilmoisturepercent);
    Serial.println("%");

  }
  timing = lastTime;
}
}
