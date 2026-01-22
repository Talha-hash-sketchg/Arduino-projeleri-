<p1>
Ben Talha bugün sizler için çeşitli projeler 
yapıcağız.

 1. projemiz herkesin ilk aldığı arduino setlerinin içinden çıkan "HCSR04" (ultrasonik mesafe sensörü).

İle mesafe ölçme kodunu yazacağız
<p1>
HCSR04 pin tanımlamaları

ECHO=dijital pin 10 

TRİG=dijital pin 9

GND=GND 

VCC=5V 

<h2>
İŞTE KOD


<h3>

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





<p1>
Şimdi ise Buton ile servo motor kontrolü yapıcağız
<h3>
Servo Motor Nedir? 
<p1>
Servo motor içindeki 5v DC motor ile yüksek tork üreten bir motordur. İçindeki dişli sistemi ile 9g veye endüstriyel olanlar 1kg
tork üretebilir.Bizim kullanacağımız Servo 
<h4>
TowerPro
SG90 
<p1>
Modeli hadi kod kısmına geçelim



