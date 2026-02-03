# Servicios de Streaming
## Memoria – Servicios en Red
### 2º ASIX

---

##  Portada

**Alumno:** Pablo Martinez Martinez 
**Asignatura:** Servicios en Red  
**Curso:** 2025 / 2026  
**Grupo:** 2º ASIX  
**Centro:** IES SERRA PERENXISAw 

---

##  Índice

1. Introducción  
2. Descarga directa vs Streaming  
3. Topologías de red  
4. TCP vs UDP  
5. Calidad de Servicio (QoS)  
6. Protocolos de Streaming  
7. Icecast2  
8. Códecs de audio  
9. Parte práctica de audio  
10. Vídeo digital  
11. Parte práctica de vídeo  
12. Prácticas completas paso a paso  
13. Conclusión  

---

## 1. Introducción

El streaming es una forma de transmitir audio o vídeo a través de una red para que el usuario pueda reproducirlo en tiempo real, sin necesidad de descargar el archivo completo.  
Actualmente se utiliza en plataformas como Spotify, YouTube, Twitch o Netflix.

---

## 2. Descarga directa vs Streaming

### Descarga directa
- El usuario descarga un archivo completo.
- El servidor envía todo el fichero aunque no se reproduzca entero.
- Consume más ancho de banda.
- Ejemplo: descarga de un vídeo o una canción.

### Streaming
- Los datos se envían poco a poco en forma de flujo.
- No se guarda el archivo completo en el dispositivo.
- Solo se envía lo que el usuario reproduce.
- Es más eficiente que la descarga directa.

---

## 3. Topologías de red

### Unicast
- Conexión uno a uno entre servidor y cliente.
- El servidor envía el stream a cada usuario.
- Poco escalable si hay muchos oyentes.

### Multicast
- El servidor envía un único stream.
- Los routers replican los paquetes.
- Se utiliza principalmente en redes internas.

---

## 4. TCP vs UDP

### TCP
- Protocolo fiable.
- Retransmite paquetes perdidos.
- Mayor latencia.
- Muy compatible con firewalls.
- Muy usado en streaming comercial.

### UDP
- No retransmite paquetes.
- Menor latencia.
- Puede haber pérdida de calidad.
- Usado en tiempo real (videollamadas).

---

## 5. Calidad de Servicio (QoS)

### Jitter
Es la variación en el tiempo de llegada de los paquetes.  
Si es alto, provoca cortes en el audio o el vídeo.

### Buffer
Memoria temporal donde se almacenan datos antes de reproducirse.
- Más buffer: más estabilidad.
- Más buffer: más retraso.

### Burst-on-Connect
Técnica usada en Icecast para enviar datos más rápido al inicio y reducir el tiempo de espera.

---

## 6. Protocolos de Streaming

### HTTP Legacy
- Usa TCP.
- Flujo continuo de datos.
- Usado en radios online como Icecast.

### HTTP Adaptativo
- Divide el contenido en fragmentos.
- Permite cambiar la calidad según la conexión.
- Usado por Netflix y YouTube.

### Real-Time
- RTMP: envío de vídeo al servidor.
- RTSP: cámaras IP.
- WebRTC: videollamadas en tiempo real.

---

## 7. Icecast2

Icecast2 es un servidor de streaming de audio de código abierto.

Características:
- Distribuye audio a muchos oyentes.
- No genera contenido.
- Soporta MP3 y OGG.
- Usa puntos de montaje como `/radio`.

---

## 8. Códecs de audio

Un códec es un algoritmo que permite comprimir y descomprimir audio.

Parámetros importantes:
- Frecuencia de muestreo.
- Profundidad de bits.
- Canales de audio.

Tipos:
- Códecs con pérdida: MP3.
- Códecs sin pérdida: WAV, FLAC.

---
## 8.1 Teoría de cálculo en servicios de streaming

En los servicios de streaming es fundamental comprender cómo se calculan el tamaño de los archivos multimedia y el consumo de ancho de banda, ya que estos factores influyen directamente en la calidad del servicio, el número de usuarios simultáneos y la carga de la red.

Tanto en audio como en vídeo, los cálculos se basan en parámetros técnicos como la frecuencia de muestreo, la profundidad de bits, el número de canales, la resolución o los fotogramas por segundo.

---

### Audio digital

El audio digital representa el sonido mediante muestras tomadas a intervalos regulares.

Los parámetros principales son:

- **Frecuencia de muestreo (Hz):** número de muestras por segundo.
- **Profundidad de bits:** número de bits usados para cada muestra.
- **Canales:** mono (1), estéreo (2), etc.
- **Bitrate:** cantidad de bits transmitidos por segundo.

#### Fórmula del bitrate de audio sin comprimir

Bitrate = Frecuencia × Profundidad de bits × Canales
---

### Tamaño de un archivo de audio

Para calcular el tamaño de un archivo de audio sin comprimir:

Tamaño (bits) = Bitrate × Duración (segundos)
Tamaño (bytes) = Tamaño (bits) / 8
---

### Audio en streaming

En streaming, el archivo no se descarga completo, pero **el ancho de banda consumido es igual al bitrate del audio** multiplicado por el número de oyentes simultáneos.

Ancho de banda total = Bitrate × Número de oyentes
---

### Vídeo digital

El vídeo digital está formado por una secuencia de imágenes (fotogramas) mostradas a gran velocidad.

Parámetros principales:

- **Resolución:** ancho × alto (por ejemplo, 1920 × 1080).
- **FPS:** fotogramas por segundo.
- **Profundidad de color:** bits por píxel.
- **Bitrate de vídeo**
- **Códec:** H.264, H.265, VP9, etc.

---

### Bitrate de vídeo sin comprimir

Bitrate = Resolución × Profundidad de color × FPS
---

### Tamaño de un archivo de vídeo

Tamaño = Bitrate × Duración
En la práctica, los códecs reducen enormemente este valor mediante compresión.

---

### Impacto en la red

En servicios de streaming, el consumo total de red depende de:

- Bitrate del contenido
- Número de usuarios conectados
- Tipo de conexión (unicast o multicast)

Una mala planificación puede provocar saturación, jitter o cortes en el servicio.

---

## 8.2 Práctica de cálculo – Servicios de Streaming

### Ejercicio 1: Cálculo del bitrate de audio sin comprimir

#### Enunciado
Calcular el bitrate de un audio con las siguientes características:
- Frecuencia de muestreo: 44 100 Hz
- Profundidad de bits: 16 bits
- Canales: 2 (estéreo)

#### Fórmula
Bitrate = Frecuencia × Bits × CanalesBitrate = 44100 × 16 × 2
Bitrate = 1 411 200 bps
---

### Ejercicio 2: Tamaño de un archivo de audio

#### Enunciado
Calcular el tamaño de un audio sin comprimir de 3 minutos con un bitrate de 1 411 200 bps.

#### Datos
Duración = 3 minutos = 180 segundos
#### Cálculo
Tamaño (bits) = 1 411 200 × 180
Tamaño (bytes) = resultado / 8
---

### Ejercicio 3: Consumo de ancho de banda en una radio online

#### Enunciado
Una radio emite audio a 128 kbps y tiene 50 oyentes simultáneos.


#### Fórmula
Ancho de banda total = Bitrate × Oyentes
#### Cálculo
Ancho de banda = 128 kbps × 50
---

### Ejercicio 4: Cálculo del bitrate de vídeo sin comprimir

#### Enunciado
Calcular el bitrate de un vídeo con:
- Resolución: 1920 × 1080
- Profundidad de color: 24 bits
- FPS: 30

#### Fórmula
Bitrate = Ancho × Alto × Bits × FPS
#### Cálculo
#### Cálculo
Bitrate = 1920 × 1080 × 24 × 30
---

### Ejercicio 5: Espacio necesario para vídeo

#### Enunciado
Calcular el espacio necesario para un vídeo de 10 minutos con un bitrate de 4 Mbps.

#### Datos
Duración = 10 minutos = 600 segundos
#### Cálculo
Tamaño (bits) = 4 000 000 × 600
Tamaño (bytes) = resultado / 8
---

### Ejercicio 6: Número máximo de usuarios

#### Enunciado
Un servidor tiene una conexión de 100 Mbps y emite vídeo a 5 Mbps por usuario.

#### Fórmula
Usuarios máximos = Ancho de banda total / Bitrate por usuario
#### Cálculo
Usuarios = 100 / 5
---

### Observaciones finales

En todos los ejercicios:
- Es importante convertir correctamente las unidades.
- Justificar cada paso del cálculo.
- Analizar si los resultados son realistas para un entorno real.


## 9. Parte práctica de audio

En esta parte se trabajan ejercicios relacionados con:
- Cálculo del tamaño de archivos de audio sin comprimir.
- Consumo de ancho de banda en streaming.
- Cálculo del bitrate.
- Número máximo de oyentes según la red.

### Pasos generales para los ejercicios
1. Leer los datos del ejercicio.
2. Identificar frecuencia, bits y canales.
3. Aplicar las fórmulas vistas en clase.
4. Convertir unidades si es necesario.
5. Justificar el resultado.

(No se incluyen resultados numéricos.)

---

## 10. Vídeo digital

El vídeo digital utiliza los mismos conceptos que el audio pero añade imagen.

Conceptos importantes:
- Resolución (1080p, 4K, 8K).
- FPS (fotogramas por segundo).
- Profundidad de color.
- Bitrate.
- Contenedor (MP4, MKV).

Un contenedor puede incluir vídeo, audio, subtítulos y metadatos.

---

## 11. Parte práctica de vídeo

En esta parte se realizan ejercicios sobre:
- Cálculo del bitrate de vídeo sin comprimir.
- Espacio necesario en disco.
- Uso del ancho de banda en streaming.

### Pasos generales
1. Anotar resolución, FPS y profundidad de color.
2. Calcular el bitrate.
3. Calcular el espacio ocupado.
4. Analizar el impacto en la red.

---

## 12. Prácticas completas paso a paso

### Práctica 1: Radio Online con Icecast2 y Mixxx

#### 1. Configuración del servidor (Ubuntu 24)

1. Crear una máquina virtual con Ubuntu 24.
2. Configurar la red en modo adaptador puente.
3. Comprobar que el sistema tiene sonido.
4. Actualizar el sistema:
   sudo apt update
6. Instalar Icecast2:
   sudo apt install icecast2
7. Configurar las contraseñas durante la instalación.
8. Acceder desde un navegador a:
   http://IP_DEL_SERVIDOR:8000
   para comprobar que el servidor funciona.

---

#### Configuración del DJ (Ubuntu 24)

1. Crear otra máquina virtual con Ubuntu 24.
2. Configurar la red en adaptador puente.
3. Comprobar el sonido.
4. Instalar Mixxx:
   sudo add-apt-repository ppa:mixxx/mixxx
sudo apt update
sudo apt install mixxx
5. Abrir Mixxx y configurar la emisión:
- Tipo: Icecast2
- IP del servidor
- Puerto: 8000
- Punto de montaje: nombre del alumno
- Usuario: source
- Contraseña: la configurada en Icecast

---

#### Comprobaciones finales

1. Acceder al servidor desde el navegador.
2. Reproducir el stream.
3. Abrir VLC.
4. Ir a *Medio → Abrir ubicación de red*.
5. Introducir la URL del stream.
6. Escuchar la radio.
7. Conectarse a la radio de otros compañeros.

---

### Práctica 2: Vídeo con FFmpeg

#### Instalación de FFmpeg
sudo apt install ffmpeg

---

#### Análisis del vídeo

1. Descargar el archivo de vídeo proporcionado.
2. Ejecutar:
ffprobe -v error -show_streams fichero.mp4
3. Identificar:
- Códec.
- Resolución.
- FPS.
- Bitrate.

---

#### Cambio de contenedor (Remuxing)

1. Ejecutar:
ffmpeg -i original.mp4 -c:v copy -c:a copy salida.mkv
2. Comprobar:
- Tamaño del archivo.
- Tiempo empleado.
- Uso de CPU.

---

#### Cambio de códecs

1. Crear una versión en H.264:
ffmpeg -i original.mp4 -c:v libx264 -b:v 2M -c:a copy h264.mp4
2. Crear una versión en H.265:
ffmpeg -i original.mp4 -c:v libx265 -b:v 2M -c:a copy h265.mp4
3. Comparar:
- Calidad de imagen.
- Aparición de artefactos.
- Tamaño del archivo.

---

#### Simulación de perfiles de streaming

1. Crear un perfil de baja calidad (móvil).
2. Crear un perfil de alta calidad (1080p).
3. Analizar:
- Espacio necesario en disco.
- Número de usuarios simultáneos posibles.

---

## 13. Conclusión

A lo largo de esta unidad se han aprendido los conceptos básicos del streaming, los protocolos más utilizados y el funcionamiento de servidores de audio y vídeo.  
Las prácticas han permitido trabajar con herramientas reales como Icecast, Mixxx y FFmpeg.


