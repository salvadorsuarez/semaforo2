# semaforo2
# UNIDAD_3
# Proyecto Arduino con LCD y Java.
>Creado por: Milton Alexis Durán Moreno

>Contacto: duran.milton.92@hotmail.com

## Arduino con un LCD desplegar.
- Mensaje
- Hora 
- Temperatura

El usuario puede navegar entre los mensajes crear una interfaz en java para mandar los mensajes al arduino, mostrando cada uno de los solicitado como la temperatura, Hora, y los mensajes que le mandemos. cada funcion con un respectivo tiempo 

Programas:
- Java
- Arduino IDE

Materiales:
- Protoboard
- Arudino UNO
- LM35 (sensor de tempatura)
- Potenciometro (10k)
- Pantalla LCD.
- Cables
- Resistencia 220 ohmios

Librerias:
- RXTXcomm
- GiovynetDriver
- jSerialComm-1.3.11
- jgsl-0.1.0-javadoc

## Diseño electrónico
![alt tag](https://github.com/MiltonDM/UNIDAD_3/blob/master/image/1.png)

## Diseño Interfaz Java
![alt tag](https://github.com/MiltonDM/UNIDAD_3/blob/master/image/interfaz%201.png)
## Vista previa de Resultados:

<table>
<tr>
<td><img src=https://github.com/MiltonDM/UNIDAD_3/blob/master/image/IMG_20180411_195835602_BURST001.jpg></td>
<td><img src=https://github.com/MiltonDM/UNIDAD_3/blob/master/image/IMG_20180411_195900047_BURST000_COVER_TOP.jpg></td>
<td><img src=https://github.com/MiltonDM/UNIDAD_3/blob/master/image/IMG_20180411_195905173_BURST000_COVER_TOP.jpg></td>
</tr>
</table>

*************************************************************************
# Brazo_Robotico_De_4_Ejes
El propósito de esta práctica es desarrollar paso a paso un proyecto para controlar y programar un Brazo Robot, simulando las funciones básicas de un robot industrial. 

# Proyecto Arduino con una interfaz en Java para Brazo .

***Integrantes Colaboradores***
>Creado por: Milton Alexis Durán Moreno.<br />
>Creado por: Luis Eduardo Hernadez Magaña.<br />
>Creado por: Jorge Alderto Sanchez Maldona.<br />

***Correo de los contactos***
>Contacto: duran.milton.92@hotmail.com<br />
>Contacto: jorgealberto_sanchezmaldonado@outlook.com <br />
>Contacto: luis.hernandez.magana@hotmail.com<br />

## El robot debe tener dos funciones básicas:
- **Programar:** Registrar las posiciones de los brazos en tres dimensiones (cada registro es un "paso", un programa consiste en una serie de pasos). 
- **Ejecutar:** Realice en secuencia las posiciones registradas en el "Programa". El robot ejecutará el programa hasta que se use el comando "ABORTAR

**Programas:**
- Java (netbeans)
- Arduino IDE

**Materiales:**
- 2 Arduinos Uno
- Protoboard.
- Driver Uln2003 .
- Motores paso a paso: 28BYJ-48.
- ServoMotor: TowerPro SG90 9G Mini.
- Potenciometro (10k).
- Pantalla LCD.
- Cables.
- Leds.
- Pulsadore (botones).
- resistencias 200 homs
- Base para poner los servos.

## Características principales: 
 - El proyecto se usa para controlar robots con  4 DOF ("Grados de libertad").
 - El robot se debe controlar en modo "REMOTO" (a través de una programa en java por medio del puerto serial).
 - La información para el usuario se podrá proporcionar a través de LEDS de colores, una pantalla LCD de 2 líneas y/ó sonido (un zumbador).
 - Debe de contener un botón de paro de emergencia (Físico).     
 - Si existe un fallo y/o corte de energía, después de restablecerse la corriente el robot debe de continuar el programa (aunque este no se encuentre conectado a la aplicación).
 - Los brazos robóticos se pueden clasificar de acuerdo con el número de "articulaciones" o "Grados de libertad" (DOF) que tienen.             
     - La "Base", o "Cintura", por lo general puede girar el brazo 180o o 360o, dependiendo del   tipo de Servo utilizado (aquí en este proyecto, se debe utilizar un motor a pasos para girar 360o)
     - El "Hombro" es el responsable de "levantar o bajar" el brazo verticalmente 
     - El "codo" hará que el brazo "avance o retroceda".
     - La "Garra" o "Pinza" funciona abriendo o cerrándose para "agarrar cosas". 

Librerias: para la comunicacion Arduino con Java

    >RXTXcomm
    >PanamaHitek_Arduino-3.0.0

## Diseño electrónico
![alt tag](https://github.com/MiltonDM/UNIDAD_3/blob/master/image/1.png)

## Diseño Interfaz Java
![alt tag](https://github.com/MiltonDM/UNIDAD_3/blob/master/image/interfaz%201.png)
## Vista previa de Resultados:

<table>
<tr>
<td><img src=https://github.com/MiltonDM/UNIDAD_3/blob/master/image/IMG_20180411_195835602_BURST001.jpg></td>
<td><img src=https://github.com/MiltonDM/UNIDAD_3/blob/master/image/IMG_20180411_195900047_BURST000_COVER_TOP.jpg></td>
<td><img src=https://github.com/MiltonDM/UNIDAD_3/blob/master/image/IMG_20180411_195905173_BURST000_COVER_TOP.jpg></td>
</tr>
</table>

## Referencias
**link:** http://panamahitek.com/arduino-java-facil-y-rapido/<br />
**link:** http://panamahitek.com/libreria-panamahitek_arduino/<br />

Semaforo peatonal
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
