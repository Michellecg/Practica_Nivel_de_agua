# Practica ESP32 con sensor ultrasónico de distancia y LCD
En este repositorio se muestra una práctica utilizando la página Wokwi. En esta simulación se añaden condiciones para un sensor ultrasónico de distancia con LED's.

## Introducción

### Descripción

En esta simulación se colocan condiciones para el sensor ultrasónico de distancia con **LED's**, es decir, dependiendo la distancia que se detecte, se prenderá un **LED**. En esta práctica se usará nuevamente el simulador [WOKWI](https://wokwi.com/).


## Material Necesario

Para realizar esta práctica se ocuparon las siguientes herramientas y componentes:

- [SIMULADOR WOKWI](https://wokwi.com/)
- Tarjeta ESP32
- Sensor ultrasónico de distancia
- 4 LED's
- 4 resistencias



## Instrucciones

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://wokwi.com/).


### Instrucciones de preparación de entorno 

1. Al ingresar a la página de [WOKWI](https://wokwi.com/) se selecciona la tarjeta ESP32, se agrega el sensor ultrasónico de distancia, 4 LED's y 4 resistencias.

2. Una vez seleccionado la tarjeta ```Esp32``` junto a los componentes, en la parte izquierda se encuentra la pestaña de código donde se agrega lo siguiente:

```
// defines pins numbers
const int trigPin = 13;
const int echoPin = 12;
const int led1 = 23;
const int led2 = 22;
const int led3 = 21;
const int led4 = 19;

// defines variables
long duration;
int distance;
int safetyDistance;


void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
}


void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
if (safetyDistance>=2 && safetyDistance<=50)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=50 && safetyDistance<=100) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=100 && safetyDistance<=150) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=150) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
}
else
{
  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
}

``` 


3. Hacer la conexión del **sensor ultrasónico de distancia**, **4 LED'S** y **4 resistencias** a la tarjeta **ESP32** como se muestra en la siguente imagen.

![](https://github.com/Michellecg/Practica_Nivel_de_agua/blob/main/Conex_Ult_LED.PNG)

### Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Modificar la distancia dando *doble click* al sensor **ultrasónico de distancia**


## Resultados

Una vez compilado el programa y que no se hayan presentado errores, se podrán visualizar que dependiendo la distancia se prenderá un LED.

![](https://github.com/Michellecg/Practica_Nivel_de_agua/blob/main/Res_Dis1.PNG)

![](https://github.com/Michellecg/Practica_Nivel_de_agua/blob/main/Res_Dis2.PNG)

![](https://github.com/Michellecg/Practica_Nivel_de_agua/blob/main/Res_Dis3.PNG)

![](https://github.com/Michellecg/Practica_Nivel_de_agua/blob/main/Res_Dis4.PNG)


# Créditos

Desarrollado por Michelle Cuatlapantzi González

- [GitHub](https://github.com/Michellecg/)