<p1>
Ben Talha bugün sizler için çeşetlili projeler 
yapıcağız.

 1. projemiz herkesin ilk aldığı arduino setlerinin içinden çıkan "HCSR04" (ultrasonik mesafe sensörü).

İle mesafe ölçme kodunu yazacağız
<p1>
HCSR04 pin tanımlamaları

ECHO=dijital pin 10 
TRİG=dijital pin 9
GND=GND 
VCC=5V 
<p1>
const int trigPin = 9;
const int echoPin = 10;

long sure;
int mesafe;

void setup() {
  pinMode(trigPin, OUTPUT); 
  pinMode(echoPin, INPUT);  
  Serial.begin(9600);
}

void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  sure = pulseIn(echoPin, HIGH);

  // burada mesafeyi ses hızına bölüyoruz
  mesafe = sure * 0.034 / 2;

  
  Serial.print("Mesafe: ");
  Serial.print(mesafe);
  Serial.println(" cm");

  // isterseniz bu değeri küçültürsen daha hızlı ölçüm alırsın (tavsiye etmem) 
  delay(200);
}


