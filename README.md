# GuitarLab-ESP32

![ESP32](https://img.shields.io/badge/ESP32-IoT-blue)
![Arduino](https://img.shields.io/badge/Arduino-C++-green)
![OLED](https://img.shields.io/badge/OLED-SSD1306-orange)

Sistema inteligente de afinación de guitarra con visualización local y monitorización web

## Descripción

Este proyecto consiste en el desarrollo de un afinador digital de guitarra en tiempo real utilizando una placa ESP32, un micrófono digital I2S (INMP441) y una pantalla OLED de 128x64 píxeles mediante comunicación I²C.

Además de la visualización local en la pantalla OLED, el sistema incorpora una interfaz web accesible desde cualquier dispositivo conectado a la misma red Wi-Fi, permitiendo consultar los datos de afinación desde un teléfono móvil o un ordenador.

---

## Funcionalidades

* Detección de la frecuencia fundamental de la señal captada por el micrófono.
* Identificación automática de la nota musical correspondiente.
* Reconocimiento de la cuerda de guitarra más próxima:

  * E2 (6ª cuerda)
  * A2 (5ª cuerda)
  * D3 (4ª cuerda)
  * G3 (3ª cuerda)
  * B3 (2ª cuerda)
  * E4 (1ª cuerda)
    
* Visualización de:

  * Frecuencia detectada
  * Nota musical
  * Cuerda identificada
  * Indicador visual de afinación
* Página web integrada para monitorización remota.
* Conexión inalámbrica mediante Wi-Fi.

---

## Componentes utilizados

* ESP32 DevKit
* Micrófono digital INMP441
* Pantalla OLED SSD1306 128x64
* Cables Dupont
* Protoboard

---

## Software y librerías

**Lenguaje utilizado**

* C, C++ (Arduino IDE)

**Librerías principales**

* U8g2
* WiFi.h
* WebServer.h
* driver/i2s.h

---


## Conexiones

| Dispositivo | Pin ESP32 / Conexión |
| ----------- | -------------------- |
| INMP441 WS  | GPIO 16              |
| INMP441 SD  | GPIO 18              |
| INMP441 SCK | GPIO 17              |
| INMP441 VDD | 3.3V                 |
| INMP441 GND | GND                  |
| INMP441 L/R | GND                  |
| OLED SDA    | GPIO 4               |
| OLED SCL    | GPIO 5               |
| OLED VCC    | 3.3V                 |
| OLED GND    | GND                  |

---

## Funcionamiento

1. El micrófono INMP441 captura el sonido de la cuerda de la guitarra.
2. El ESP32 recibe las muestras digitales mediante el protocolo I2S.
3. Se procesa la señal para estimar la frecuencia predominante.
4. Se calcula la nota musical asociada a dicha frecuencia.
5. El sistema determina cuál es la cuerda de guitarra más cercana.
6. La información se muestra simultáneamente en la pantalla OLED y en la página web.

---

## Interfaz Web

La interfaz web muestra en tiempo real:

* Frecuencia detectada (Hz)
* Nota musical
* Cuerda identificada
* Mensaje informativo para el usuario

La actualización de los datos se realiza automáticamente sin necesidad de recargar la página.

---

## Ejemplo de visualización

### OLED

```text
110.0 Hz
A2 (5ª)

◀────■────▶
```

### Página web

* Frecuencia: 110.0 Hz
* Nota: A2
* Cuerda: A2 (5ª)
* Actualización automática

---

## Autora

Ainhoa Dumitru
