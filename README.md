<p1>
Ben Talha bugün sizler için çeşetlili projeler 
yapıcağız.

 1. projemiz herkesin ilk aldığı arduino setlerinin içinden çıkan "HCSR04" (ultrasonik mesafe sensörü).

İle mesafe ölçme kodunu yazacağı
<h1>
/*
  HC-SR04 Mesafe Sensörü Kullanımı
  Bu kod, sensörden gelen veriyi cm cinsinden Seri Port ekranına yazdırır.
*/

// Pin tanımlamaları
const int trigPin = 9;
const int echoPin = 10;

// Değişkenler
long sure;
int mesafe;

void setup() {
  // Pin modlarını ayarlıyoruz
  pinMode(trigPin, OUTPUT); // Ses dalgası gönderen pin
  pinMode(echoPin, INPUT);  // Yankıyı alan pin
  
  // Sonuçları görmek için seri iletişimi başlatıyoruz
  Serial.begin(9600);
}

void loop() {
  // 1. Sensörü temizlemek için Trig pinini düşük konuma getiriyoruz
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  // 2. 10 mikrosaniye boyunca ses dalgası gönderiyoruz
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // 3. Echo pininden dönen sinyalin süresini mikrosaniye olarak ölçüyoruz
  sure = pulseIn(echoPin, HIGH);

  // burada mesafeyi is
  mesafe = sure * 0.034 / 2;

  
  Serial.print("Mesafe: ");
  Serial.print(mesafe);
  Serial.println(" cm");

  // isterseniz bu değeri küçültürsen daha hızlı ölçüm alırsın (tavsiye etmem) 
  delay(200);
}


