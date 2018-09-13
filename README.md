# semaforo2

>Creado por: Diego Salvador Suarez Quijas

>Contacto: d.salvador0604@gmail.com

## Arduino con LED`s y Zumbador.
- Sonido
- Ensender LED`s

## Practica 1
Realizar un sistema que simule un Semáforo Interactivo usando Arduino. Este debe mostrar un conjunto de semáforos que cambiarán de verde a ámbar a rojo, y viceversa, luego de un período de tiempo establecido, utilizando el sistema de cuatro estados de los semáforos en México. Este se extiende para incluir un conjunto de luces y un botón peatonal para solicitar cruzar la calle.
Cuando llega el peatón y se dispone a cruzar pulsa el botón que encuentra en la parte baja del semáforo, este reconoce la orden y cierra el paso de los vehículos para que el viandante pueda cruzar con seguridad hasta el otro lado de la calle. Una vez que se acaba el tiempo estipulado para que el peatón cruce, ese semáforo permanecerá abierto para mejorar la movilidad de los vehículos.
El sistema deberá de contener una perilla para controlar el tiempo mínimo en que el semáforo vehicular va a durar en verde.


Programas:
- Arduino IDE

Materiales:
- Protoboard
- Arudino UNO
- LED`s
- zumbador
- Cables
- Resistencia 220 ohmios

************************************************************************* 

## Semaforo peatonal

int carRed = 12; 
int carYellow = 11;
int carGreen = 10;
int pedRed = 9; 
int pedGreen = 8;
int button = 2;
int buzzer= 13;
int crossTime = 5000;
unsigned long changeTime;
void setup() {
pinMode(carRed, OUTPUT);
pinMode(carYellow, OUTPUT);
pinMode(carGreen, OUTPUT);
pinMode(pedRed, OUTPUT);
pinMode(pedGreen, OUTPUT);
pinMode(button, INPUT);
pinMode(buzzer,OUTPUT);
digitalWrite(carGreen, HIGH);
digitalWrite(pedRed, HIGH);
}
void loop() {
int state = digitalRead(button);
if (state == HIGH && (millis() - changeTime) > 5000) {

changeLights();
}
}
void changeLights() {
digitalWrite(carGreen, LOW);
digitalWrite(carYellow, HIGH);
delay(2000); // wait 2 seconds
digitalWrite(carYellow, LOW); 
digitalWrite(carRed, HIGH);
delay(1000); 
digitalWrite(pedRed, LOW); 
digitalWrite(pedGreen, HIGH); 
delay(crossTime); 
for (int x=0; x<10; x++) {
digitalWrite(pedGreen, HIGH);
tone(buzzer,500);
delay(250);
digitalWrite(pedGreen, LOW);
noTone(buzzer);
delay(250);
}
digitalWrite(pedRed, HIGH);
delay(500);
digitalWrite(carYellow, HIGH); 
digitalWrite(carRed, LOW); 
delay(1000);
digitalWrite(carGreen, HIGH);
digitalWrite(carYellow, LOW); 
changeTime = millis();
}
