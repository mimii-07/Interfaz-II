# Interfaz II
1.[Ejercicio n°1 Arduino: "Hola Mundo"](#ejercicio-n1-arduino-hola-mundo) <br>
2.[Ejercicio n°2: Led parpadeante (Blink)](#ejercicio-n2-led-parpadeante-blink) <br>
3.[Ejercicio n°3: LED pulsador](h#ejercicio-n3-led-pulsador) <br>
4.[Ejercicio n°4: Led potenciometro](#ejercicio-n4-led-potenciometro) <br>
5.[Ejercicio n°5 Arduino: "Semaforo"](#ejercicio-n5-arduino-semaforo) <br>
6.[Ejercicio n°6: "Arduino Processing"](#ejercicio-n6-arduino-processing) <br>
7.[Ejercicio n°7: "Arduino+Boton+Processing"](#ejercicio-n7-arduinobotonprocessing) <br>
8.[Ejercicio n°8: "Arduino+Boton+Potenciometro+Processing"](#ejercicio-n8-arduinobotonpotenciometroprocessing) <br>
9.[Ejercicio n°9: "If + Else"](#ejercicio-n9-if--else) <br>
10.[Ejercicio n°10: "Botonera"](#ejercicio-n10-botonera) <br>
11.[Ejercicio con nota: "Led pulsador modificado (intercambio de luces)"](#ejercicio-con-nota-led-pulsador-modificado-intercambio-de-luces) <br>
12.[Ejercicio n°12: "Sensor Sharp"](https://github.com/mimii-07/Interfaz-II/tree/main?tab=readme-ov-file#ejercicio-n12-sensor-sharp) <br>


### Ejercicio n°1 Arduino: "Hola Mundo"

```js
void setup() {
  Serial.begin(9600); // Inicia la comunicación serie a 9600 bps
  Serial.println("Holaaa");
  Serial.println("Adios");
}

void loop() {
  // No es necesario poner nada en el loop para este ejemplo
}
```
### Ejercicio n°2: LED Parpadeante (Blink)
```js
void setup() {  // Configuración inicial (ej: pines como entrada/salida)
  pinMode(13, OUTPUT);  // Pin 13 como salida
  pinMode(8, OUTPUT);
}

void loop() {   // Se repite infinitamente
  digitalWrite(13, HIGH);  // Encender LED
  delay(500);             // Esperar 1 segundo
  digitalWrite(13, LOW);   // Apagar LED
  //delay(500);             // Esperar 1 segundo
  digitalWrite(8, HIGH);
  delay(1000);
  digitalWrite(8,LOW);
  //delay(1000);
}
```
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/Led%20parpadeante.png" width="1024" height="550" /> 
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/IMG_9634.jpg" width="1024" height="550"/>

### Ejercicio n°3: LED pulsador
```js
void setup() {
  pinMode(2, INPUT);  // Botón como entrada
  pinMode(13, OUTPUT);
}
void loop() {
  if (digitalRead(2) == HIGH) {  // Si se presiona el botón
    digitalWrite(13, HIGH);
  } else {
    digitalWrite(13, LOW);
  }
}
```
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/Led%20pulsador.png" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/pulsador.jpeg" width="1024" height="550" />

### Ejercicio n°4: Led potenciometro
```js
void setup() {
  pinMode(9, OUTPUT);  // Pin PWM (símbolo ~)
}
void loop() {
  int valor = analogRead(A0);           // Leer potenciómetro (0-1023)
  int brillo = map(valor, 0, 1023, 0, 255);  // Convertir a rango PWM
  analogWrite(9, brillo);               // Ajustar brillo
}
```
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/Led%20ponteciometro.png" width="1024" height="550" />

### Ejercicio n°5 Arduino: "Semaforo"
```js
// C++ code - Semáforo Autos y Peatones

// Definición de pines
int LED_1 = 6;  // Luz roja autos
int LED_2 = 7;  // Luz amarilla autos
int LED_3 = 8;  // Luz verde autos
int LED_4 = 9;  // Luz verde peatones
int LED_5 = 10; // Luz roja peatones

void setup() {
  // Configuramos todos los pines como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);
}

void loop() {
  // 🚦 Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  // 🚦 Fase 3: Rojo autos, verde peatones
  digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
  digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(1000); // 5 segundos
  digitalWrite(LED_4, LOW);
  delay(1000);
  digitalWrite(LED_4, HIGH);
  delay(1000);
  digitalWrite(LED_4, LOW);
  delay(1000);
  digitalWrite(LED_1, LOW);

  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  //digitalWrite(LED_4, LOW);   // Verde peatones apagado
  //digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(2000); // 2 segundos
}
}
```
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/Semaforo.png" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/IMG_9635.jpg" width="1024" height="550" />

### Ejercicio n°6: "Arduino Processing"
```js
import processing.serial.*;

Serial myPort;  // Crear objeto de la clase Serial
static String val;    // Datos recibidos desde el puerto serial
int sensorVal = 0;

void setup()
{
  background(0); 
  //fullScreen(P3D);
   size(1080, 720);
   noStroke();
  noFill();
  String portName = "COM3";// Cambia el número (en este caso) para que coincida con el puerto correspondiente conectado a tu Arduino. 

  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort = new Serial(this, Serial.list()[0], 9600);

}

void draw()
{
  if ( myPort.available() > 0) {  // Si hay datos disponibles,
  val = myPort.readStringUntil('\n'); 
  try {
   sensorVal = Integer.valueOf(val.trim());
  }
  catch(Exception e) {
  ;
  }
  println(sensorVal); // léelos y guárdalos en vals!
  }  
 //background(0);
  // Escala el valor de mouseX de 0 a 640 a un rango entre 0 y 175
  float c = map(sensorVal, 0, width, 0, 400);
  // Escala el valor de mouseX de 0 a 640 a un rango entre 40 y 300
  float d = map(sensorVal, 0, width, 40,500);
  fill(255, c, 0);
  ellipse(width/2, height/2, d, d);
  ellipse(width/5, height/6, d, d);
  ellipse(width/4, height/1, d, d);
  ellipse(width/1, height/4, d, d);
  ellipse(width/1, height/1.5, d, d);
}
```
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/Arduino%20Processing.png" width="1024" height="550" />

### Ejercicio n°7: "Arduino+Boton+Processing"
##### Codigo Arduino
```js
int buttonPin = 2;  // Pin del botón
int buttonState = 0;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // Botón con resistencia interna
  Serial.begin(9600);
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH) {   // Botón presionado
    Serial.println(1);        // Enviar un "1" a Processing
    delay(200);               // Evitar rebotes
  }
}
```
##### Codigo Processing
```js
import processing.serial.*;

Serial myPort;
ArrayList<PVector> circles; 

void setup() {
  size(1920, 1080);
  background(0);
  
  // Ajusta el nombre del puerto según tu Arduino
  println(Serial.list());
  myPort = new Serial(this, "COM3", 9600);
  //myPort = new Serial(this, Serial.list()[0], 9600);
  
  circles = new ArrayList<PVector>();
}

void draw() {
  //background(0);
  
  // Dibujar círculos almacenados
  fill(random(223), random(82), random(30,200), 10);
  //noStroke();
  stroke(250, 250, 250, 50);
  for (PVector c : circles) {
    ellipse(c.x, c.y, random (30, 200), random(30,330));
  }
  
  // Revisar si llega algo de Arduino
  if (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.equals("1")) {
        // Cada vez que se aprieta el botón, agregar un círculo en posición aleatoria
        circles.add(new PVector(random(width), random(height)));
      }
    }
  }
}
```
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/botonprocessing.png" width="1024" height="550" />

### Ejercicio n°8: "Arduino+Boton+Potenciometro+Processing"
##### Codigo Arduino
```js
int buttonPin = 2;       // Pin del botón
int potPin = A0;         // Pin del potenciómetro
int buttonState = 0;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // Botón con resistencia interna
  Serial.begin(9600);
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH) {   // Botón presionado
    int potValue = analogRead(potPin);   // 0 - 1023
    Serial.print("BTN,");     // etiqueta para Processing
    Serial.println(potValue); // mando el valor junto con el evento
    delay(200);               // debounce simple
  }
}
```
##### Codigo Processing
```js
void draw() {
  //background(0);
  
  // Dibujar todos los círculos guardados
  //fill(0, 150, 255);
  //noStroke();
  fill(random(16), random(176), random(196,200), 10);
  stroke(255, 250, 250, 50);
  for (CircleData c : circles) {
    ellipse(c.x, c.y, random(c.size), random(c.size));
  }
  
  // Leer datos de Arduino
  if (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.startsWith("BTN")) {
        // Extraer el valor del potenciómetro
        String[] parts = split(val, ',');
        if (parts.length == 2) {
          float potVal = float(parts[1]);
          float circleSize = map(potVal, 0, 1023, 10, 100); // tamaño 10-100 px
          circles.add(new CircleData(random(width), random(height), circleSize));
        }
      }
    }
  }
}

// Clase para guardar datos de cada círculo
class CircleData {
  float x, y, size;
  CircleData(float x, float y, float size) {
    this.x = x;
    this.y = y;
    this.size = size;
  }
}
```
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/botonpotenciometro.png" width="1024" height="550" />

### Ejercicio n°9: "If + Else"
```js
int leds[] = {2, 3, 4, 5}; // Creamos un arreglo con los pines donde van conectados los LEDs

void setup() {
  // Esta función corre solo una vez al iniciar Arduino
  for (int i = 0; i < 4; i++) {         // Recorre el arreglo desde i = 0 hasta i = 3
    pinMode(leds[i], OUTPUT);           // Configura cada pin del arreglo como salida (para controlar LEDs)
  }
}

void loop() {
  // Esta función corre en bucle infinito
  for (int i = 0; i < 4; i++) {         // Recorre los 4 LEDs, uno por uno
    if (i % 2 == 0) {                   // Si el índice es par (0, 2)...
      digitalWrite(leds[i], HIGH);      // Enciende el LED correspondiente
    } else {                            // Si el índice es impar (1, 3)...
      digitalWrite(leds[i], LOW);       // Apaga el LED correspondiente
    }
    delay(500);                         // Espera 0,5 segundos antes de pasar al siguiente
  }
}
```
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/Captura%20de%20pantalla%202025-09-23%20133146.png" width="1024" height="550" />

### Ejercicio n°10: "Botonera"
##### Código Arduino
```js
// --- Configuración de botones ---
const int numButtons = 3;
const int buttonPins[numButtons] = {2, 4, 7};
const int ledButtonPins[numButtons] = {9, 10, 11}; // LEDs botones

// --- Configuración de potenciómetros ---
const int numPots = 2;
const int potPins[numPots] = {A0, A1};
const int ledPotPins[numPots] = {3, 5}; // LEDs PWM

// Variables de estados previos
int lastButtonState[numButtons];
int lastPotValue[numPots];

void setup() {
  Serial.begin(9600);

  // Configurar botones y LEDs
  for (int i = 0; i < numButtons; i++) {
    pinMode(buttonPins[i], INPUT_PULLUP);
    pinMode(ledButtonPins[i], OUTPUT);
    lastButtonState[i] = digitalRead(buttonPins[i]);
  }

  // Configurar LEDs de potenciómetros
  for (int i = 0; i < numPots; i++) {
    pinMode(ledPotPins[i], OUTPUT);
    lastPotValue[i] = analogRead(potPins[i]);
  }
}

void loop() {
  // Leer y enviar botones
  for (int i = 0; i < numButtons; i++) {
    int buttonState = digitalRead(buttonPins[i]);

    // LED se enciende cuando botón está presionado
    digitalWrite(ledButtonPins[i], buttonState == LOW ? HIGH : LOW);

    if (buttonState != lastButtonState[i]) {  // enviar cambios
      Serial.print("B");
      Serial.print(i); 
      Serial.print(":");
      Serial.println(buttonState);
      lastButtonState[i] = buttonState;
    }
  }

  // Leer y enviar potenciómetros
  for (int i = 0; i < numPots; i++) {
    int potValue = analogRead(potPins[i]); // 0–1023
    int pwmValue = potValue / 4;           // 0–255

    // Ajustar LED según valor
    analogWrite(ledPotPins[i], pwmValue);

    if (abs(pwmValue - lastPotValue[i]) > 2) { // evitar ruido
      Serial.print("P");
      Serial.print(i);
      Serial.print(":");
      Serial.println(pwmValue);
      lastPotValue[i] = pwmValue;
    }
  }

  delay(10);
}
```
##### Código Processing
```js
// Importamos librería para comunicación serial
import processing.serial.*;
// Importamos librería Minim para manejar audio
import ddf.minim.*;

// Declaramos el objeto serial para comunicarnos con Arduino
Serial myPort;
// Objeto principal de Minim
Minim minim;
// Array de reproductores de audio (3 pistas)
AudioPlayer[] players;
// Variable para guardar el índice de la pista que está sonando
int currentTrack = -1;  // -1 significa que no hay pista activa al inicio

void setup() {
  size(400, 200); // Ventana de 400x200 píxeles
  
  // --- Configuración del puerto serial ---
  printArray(Serial.list()); // Muestra en consola la lista de puertos disponibles
  myPort = new Serial(this, Serial.list()[0], 9600); // Abrimos el primer puerto de la lista a 9600 baudios
  
  // --- Configuración de audio ---
  minim = new Minim(this); // Inicializamos Minim
  players = new AudioPlayer[3]; // Creamos un array de 3 reproductores
  
  // Cargamos los 3 archivos de audio desde la carpeta "data"
  players[0] = minim.loadFile("audio1.mp3", 2048); 
  players[1] = minim.loadFile("audio2.mp3", 2048); 
  players[2] = minim.loadFile("audio3.mp3", 2048); 
}

void draw() {
  background(0); // Fondo negro
  fill(255);     // Color blanco para el texto
  textSize(16);  // Tamaño del texto
  
  // Mostramos en pantalla qué botón está activo
  text("Botón actual: " + (currentTrack == -1 ? "ninguno" : currentTrack), 20, 40);
}

void serialEvent(Serial myPort) {
  // Leemos la cadena que llega desde Arduino hasta el salto de línea
  String inString = trim(myPort.readStringUntil('\n'));
  
  // Si no llega nada, salimos
  if (inString == null) return;

  // --- Si el mensaje recibido empieza con "B" significa que es un botón ---
  if (inString.startsWith("B")) {
    // Quitamos la letra "B" y separamos el mensaje en partes (ejemplo "0:0")
    String[] parts = split(inString.substring(1), ':');
    
    // Si realmente recibimos dos partes (índice y estado)
    if (parts.length == 2) {
      int buttonIndex = int(parts[0]); // Número del botón (0,1,2)
      int state = int(parts[1]);       // Estado del botón (0 = presionado, 1 = suelto)
      
      // Si el botón fue presionado (LOW = 0 en Arduino)
      if (state == 0) { 
        playTrack(buttonIndex); // Llamamos a la función para reproducir la pista correspondiente
      }
    }
  }
}

// --- Función que reproduce una pista según el botón ---
void playTrack(int index) {
  // Si ya había una pista sonando, la pausamos y la rebobinamos al inicio
  if (currentTrack != -1 && players[currentTrack].isPlaying()) {
    players[currentTrack].pause();
    players[currentTrack].rewind();
  }
  
  // Reproducimos en bucle la pista seleccionada
  players[index].loop();
  
  // Actualizamos la variable para saber cuál es la pista activa
  currentTrack = index;
}
```
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/Captura%20de%20pantalla%202025-09-23%20134418.png" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/PHOTO-2025-09-23-13-38-29.jpg" width="1024" height="550" />

### Ejercicio con nota: "Led pulsador modificado (intercambio de luces)"
##### Código Arduino
```js
void setup() {
  pinMode(2, INPUT);  // Botón como entrada
  pinMode(13, OUTPUT);
  pinMode(12, OUTPUT);
}
void loop() {
  if (digitalRead(2) == HIGH) {  // Si se presiona el botón
    digitalWrite(13, HIGH);
    digitalWrite(12, LOW);
  } else {
    digitalWrite(13, LOW);
    digitalWrite(12, HIGH);
  }
}
```
##### Explicación del ejercicio y la modificación
```js
Comencé copiando el código original:
void setup() {
  pinMode(2, INPUT);  // Botón como entrada
  pinMode(13, OUTPUT);
}
void loop() {
  if (digitalRead(2) == HIGH) {  // Si se presiona el botón
    digitalWrite(13, HIGH);
  } else {
    digitalWrite(13, LOW);
  }
}
Ese, luego le agregue al void setup: 
  pinMode(12, OUTPUT);
Esto para agregar una nueva luz led a la placa y al código. Luego agregue lo siguiente al void loop:
 digitalWrite(12, LOW);
} else {
 digitalWrite(12, HIGH);
Esto es para indicar que cuando la luz que conecta en el 12 (Blanco) se apague cuando la luz del 13 (verde) prenda, y viceversa.
Conseguí lo que buscaba que era agregar una luz y que vayan intercambiando.
Todo esto fue un poco a prueba y error ya que no sabía cómo hacer que un solo botón mandara dos luces led. Finalmente describir que podía hacer una conexión o puente. Conecto un cable del botón a la placa en la parte positiva para que hacer puente y ahí poder conectar un cable que lleve la señal de ambas luces al Arduino a la entrada 2.
```
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/Captura%20de%20pantalla%202025-09-30%20125438.png" width="1024" height="550"/>
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/IMG_9636.jpeg" width="1024" height="550"/>
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/IMG_9638.jpeg" width="1024" height="550"/>

### Ejercicio n°12: Sensor Sharp
#### Codigo Arduino
```js
// Definir el pin del sensor Sharp
int sharpPin = A0;

void setup() {
  Serial.begin(9600); // Iniciar comunicación serial
}

void loop() {
  int sensorValue = analogRead(sharpPin); // Leer valor del sensor
  Serial.println(sensorValue); // Enviar valor a Processing
  delay(100); // Esperar un momento
}
```
#### Codigo Processing
```js
import processing.serial.*;

Serial myPort;  // Create object from Serial class
static String val;    // Data received from the serial port
int sensorVal = 0;

void setup()
{
  background(0); 
  //fullScreen(P3D);
   size(1080, 720);
   noStroke();
  noFill();
  String portName = "COM5";// Change the number (in this case ) to match the corresponding port number connected to your Arduino. 

  myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
}

void draw()
{
  if ( myPort.available() > 0) {  // If data is available,
  val = myPort.readStringUntil('\n'); 
  try {
   sensorVal = Integer.valueOf(val.trim());
  }
  catch(Exception e) {
  ;
  }
  println(sensorVal); // read it and store it in vals!
  }  
 //background(0);
  // Scale the mouseX value from 0 to 640 to a range between 0 and 175
  float c = map(sensorVal, 0, width, 0, 400);
  // Scale the mouseX value from 0 to 640 to a range between 40 and 300
  float d = map(sensorVal, 0, width, 40,500);
  fill(255, c, 0);
  ellipse(width/2, height/2, d, d);   

}
```
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/SENSOR%20SHARP.jpeg" width="1024" height="550"/>

### Ejercicio n°13: Sensor humedad
#### Codigo Arduino
```js
void setup()
{
  Serial.begin(9600);// abre el puerto serial y Establece la velocidad en baudios a 9600 bps
}
void loop()
{
  int sensorValue;
  sensorValue = analogRead(0);   //conectar el sensor de humedad al pin analogo 0
  Serial.println(sensorValue); //imprime el valor a serial.
  delay(200);
}
```
#### Codigo Processing
```js
// --- Librerías necesarias ---
import processing.serial.*;
import processing.video.*;

// --- Variables de cámara y serial ---
Capture cam;
Serial myPort;

// --- Variables del sensor ---
float sensorValue = 0;
float suavizado = 0;

// --- Parámetros para detección de silueta ---
float umbral = 100; // controla el contraste para definir la silueta

void setup() {
  size(1280, 720);
  background(0);
  
  // --- Inicializar cámara ---
  String[] cameras = Capture.list();
  if (cameras.length == 0) {
    println("No se encontró cámara.");
    exit();
  } else {
    println("Cámara encontrada: " + cameras[0]);
    cam = new Capture(this, cameras[0]);
    cam.start();
  }
  
  // --- Inicializar puerto serie (Arduino) ---
  // Puedes ver la lista de puertos con println(Serial.list());
  String portName = Serial.list()[0]; 
  myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  //myPort = new Serial(this, portName, 9600);
}

void draw() {
  background(0);
  
  // --- Leer datos del sensor ---
  while (myPort.available() > 0) {
    String inString = trim(myPort.readStringUntil('\n'));
    if (inString != null) {
      sensorValue = float(inString);
      suavizado = lerp(suavizado, sensorValue, 0.1);
    }
  }
  
  // --- Mapear los valores del sensor ---
  float escala = map(suavizado, 0, 1023, 1.5, 0.5); // tamaño de la silueta
  float alpha = map(suavizado, 0, 1023, 255, 80);   // opacidad según distancia
  
  // --- Captura de video ---
  if (cam.available()) {
    cam.read();
  }

  // --- Dibujar silueta desde la cámara ---
  cam.loadPixels();
  loadPixels();
  
  for (int y = 0; y < cam.height; y++) {
    for (int x = 0; x < cam.width; x++) {
      int loc = x + y * cam.width;
      color c = cam.pixels[loc];
      float brillo = brightness(c);
      
      // Si el brillo es menor que el umbral, dibujamos píxel blanco (silueta)
      if (brillo < umbral) {
        int px = int(x * escala);
        int py = int(y * escala);
        if (px < width && py < height) {
          stroke(255, alpha);
          point(px, py);
        }
      }
    }
  }
}
```
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/SENSOR%20HUMEDAD.jpeg width="1024" height="550"/>

### Ejercicio n°14: Cuerpo, video, sensor sharp.
#### Codigo Arduino
```js
// --- Sensor Sharp conectado al pin A0 ---
int sensorPin = A0;
int valor;

void setup() {
  Serial.begin(9600);
}

void loop() {
  valor = analogRead(sensorPin);
  Serial.println(valor);
  delay(50); // envío cada 50 ms
}
```
#### Codigo Processing
```js
// --- Librerías necesarias ---
import processing.serial.*;
import processing.video.*;

// --- Variables de cámara y serial ---
Capture cam;
Serial myPort;

// --- Variables del sensor ---
float sensorValue = 0;
float suavizado = 0;

// --- Parámetros para detección de silueta ---
float umbral = 100; // controla el contraste para definir la silueta

void setup() {
  size(1280, 720);
  background(0);
  
  // --- Inicializar cámara ---
  String[] cameras = Capture.list();
  if (cameras.length == 0) {
    println("No se encontró cámara.");
    exit();
  } else {
    println("Cámara encontrada: " + cameras[0]);
    cam = new Capture(this, cameras[0]);
    cam.start();
  }
  
  // --- Inicializar puerto serie (Arduino) ---
  // Puedes ver la lista de puertos con println(Serial.list());
  String portName = Serial.list()[0]; 
  myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  //myPort = new Serial(this, portName, 9600);
}

void draw() {
  background(0);
  
  // --- Leer datos del sensor ---
  while (myPort.available() > 0) {
    String inString = trim(myPort.readStringUntil('\n'));
    if (inString != null) {
      sensorValue = float(inString);
      suavizado = lerp(suavizado, sensorValue, 0.1);
    }
  }
  
  // --- Mapear los valores del sensor ---
  float escala = map(suavizado, 0, 1023, 1.5, 0.5); // tamaño de la silueta
  float alpha = map(suavizado, 0, 1023, 255, 80);   // opacidad según distancia
  
  // --- Captura de video ---
  if (cam.available()) {
    cam.read();
  }

  // --- Dibujar silueta desde la cámara ---
  cam.loadPixels();
  loadPixels();
  
  for (int y = 0; y < cam.height; y++) {
    for (int x = 0; x < cam.width; x++) {
      int loc = x + y * cam.width;
      color c = cam.pixels[loc];
      float brillo = brightness(c);
      
      // Si el brillo es menor que el umbral, dibujamos píxel blanco (silueta)
      if (brillo < umbral) {
        int px = int(x * escala);
        int py = int(y * escala);
        if (px < width && py < height) {
          stroke(255, alpha);
          point(px, py);
        }
      }
    }
  }
}
```
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/IMG_2112.jpeg" width="1024" height="550"/>
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/Captura%20de%20pantalla%202025-10-21%20130905.png" width="1024" height="550"/>

### Ejercicio N°15: Promedio de imagenes
#### Codigo arduino
```js
void setup() {
  Serial.begin(9600);
}

void loop() {
  int potValue = analogRead(A0);
  Serial.println(potValue);
  delay(20);
}
```
#### Codigo processing
```js
import processing.serial.*;

Serial myPort;
PImage[] imgs;
int numImages = 7;
PImage avgImg;
float mixAmount = 0;

void setup() {
  size(1800, 1600);
  println(Serial.list());
  
  //Cambia el índice según tu puerto (0, 1, 2, etc.)
  myPort = new Serial(this, Serial.list()[0], 9600);
  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort.bufferUntil('\n');

  // Cargar imágenes
  imgs = new PImage[numImages];
  imgs[0] = loadImage("img1.jpg");
  imgs[1] = loadImage("img2.jpg");
  imgs[2] = loadImage("img3.jpg");
  imgs[3] = loadImage("img4.jpg");
  imgs[4] = loadImage("img5.jpg");
  imgs[5] = loadImage("img6.jpg");
  imgs[6] = loadImage("img7.jpg");

  avgImg = createImage(imgs[0].width, imgs[0].height, RGB);
}

void draw() {
  // Dibujar la imagen promedio según el valor del potenciómetro
  background(0);
  calcAverage(mixAmount);
  image(avgImg, 0, 0, width, height);
  
  fill(255);
  textSize(20);
  text("Mezcla: " + nf(mixAmount, 1, 2), 20, height - 20);
}

void serialEvent(Serial p) {
  String val = p.readStringUntil('\n');
  if (val != null) {
    val = trim(val);
    float sensor = float(val);
    mixAmount = map(sensor, 0, 1023, 0, 7); // 0 a 1
  }
}

void calcAverage(float t) {
  avgImg.loadPixels();

  for (int i = 0; i < avgImg.pixels.length; i++) {
    color c1 = imgs[0].pixels[i];
    color c2 = imgs[1].pixels[i];
    color c3 = imgs[2].pixels[i];

    // Promedio ponderado según el potenciómetro
    float r = red(c1)*(1-t) + red(c2)*t*0.5 + red(c3)*t*0.5;
    float g = green(c1)*(1-t) + green(c2)*t*0.5 + green(c3)*t*0.5;
    float b = blue(c1)*(1-t) + blue(c2)*t*0.5 + blue(c3)*t*0.5;

    avgImg.pixels[i] = color(r, g, b);
  }
  avgImg.updatePixels();
}
```
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/IMG_2115.jpeg" width="1024" height="550"/>
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/Captura%20de%20pantalla%202025-10-21%20133248.png" width="1024" height="550"/>

### Segunda entrega:"Cuerpo, video, sensor sharp" modificado
#### Codigo arduino
```js
// --- Sensor Sharp conectado al pin A0 ---
int sensorPin = A0;
int valor;

void setup() {
  Serial.begin(9600);
}

void loop() {
  valor = analogRead(sensorPin);
  Serial.println(valor);
  delay(50); // envío cada 50 ms
}
```
#### Codigo Processing
```js
// --- Librerías necesarias ---
import processing.serial.*;
import processing.video.*;

// --- Variables de cámara y serial ---
Capture cam;
Serial myPort;

// --- Variables del sensor ---
float sensorValue = 0;
float suavizado = 0;

// --- Parámetros para detección de silueta ---
float umbral = 100;
String simbolos = "@#%*+=-:. ";

PGraphics buffer; // para dibujar la cámara una vez

void setup() {
  size(1280, 720);
  background(0);
  textAlign(CENTER, CENTER);
  textSize(8);
  colorMode(HSB, 255);
  
  // --- Inicializar cámara ---
  String[] cameras = Capture.list();
  if (cameras.length == 0) {
    println("No se encontró cámara.");
    exit();
  } else {
    println("Cámara encontrada: " + cameras[0]);
    cam = new Capture(this, cameras[0]);
    cam.start();
  }
  
  // --- Inicializar puerto serie (Arduino) ---
  String portName = Serial.list()[0]; 
  myPort = new Serial(this, portName, 9600);

  buffer = createGraphics(640, 360); // buffer donde dibujamos la cámara procesada
}

void draw() {
  background(0);
  
  // --- Leer datos del sensor ---
  while (myPort.available() > 0) {
    String inString = trim(myPort.readStringUntil('\n'));
    if (inString != null) {
      sensorValue = float(inString);
      suavizado = lerp(suavizado, sensorValue, 0.1);
    }
  }

  // --- Mapear valores del sensor ---
  float escala = map(suavizado, 0, 1023, 1.5, 0.5);  // zoom central
  float alpha = map(suavizado, 0, 1023, 255, 100);   // opacidad
  float tonoBase = map(suavizado, 0, 1023, 0, 255);  // tono
  int repeticiones = int(map(suavizado, 0, 1023, 1, 6)); // número de mosaicos

  // --- Captura de video ---
  if (cam.available()) cam.read();
  cam.loadPixels();

  // --- Dibujar una sola vez la cámara al buffer ---
  buffer.beginDraw();
  buffer.background(0);
  buffer.textAlign(CENTER, CENTER);
  buffer.textSize(8);
  buffer.colorMode(HSB, 255);
  
  buffer.pushMatrix();
  buffer.translate(buffer.width/2, buffer.height/2);
  buffer.scale(escala);
  buffer.translate(-cam.width/2, -cam.height/2);

  for (int y = 0; y < cam.height; y += 4) {
    for (int x = 0; x < cam.width; x += 4) {
      int loc = x + y * cam.width;
      color c = cam.pixels[loc];
      float brillo = brightness(c);
      int index = int(map(brillo, 0, 255, 0, simbolos.length() - 1));
      char simbolo = simbolos.charAt(index);
      
      if (brillo < umbral) {
        float tono = (tonoBase + map(x, 0, cam.width, 0, 60)) % 255;
        buffer.fill(tono, 255, 255, alpha);
        buffer.text(simbolo, x, y);
      }
    }
  }

  buffer.popMatrix();
  buffer.endDraw();

  // --- Dibujar mosaico en pantalla ---
  float tileW = width / float(repeticiones);
  float tileH = height / float(repeticiones);

  for (int i = 0; i < repeticiones; i++) {
    for (int j = 0; j < repeticiones; j++) {
      image(buffer, i * tileW, j * tileH, tileW, tileH);
    }
  }
}
```
#### circuito
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/fisico.jpeg" width="1024" height="550"/>
#### Resultados
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/registro%201.png" width="1024" height="550"/>
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/registro%202.png" width="1024" height="550"/>
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/registro%203.png" width="1024" height="550"/>
<img src="https://raw.githubusercontent.com/mimii-07/Interfaz-II/refs/heads/main/img/registro%204.png" width="1024" height="550"/>
