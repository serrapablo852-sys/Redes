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
# 📘 Fórmulas del PDF – Streaming, Audio y Vídeo

---

# 🎧 AUDIO

## Cálculo de peso (audio sin compresión)
**Fórmula dada en el PDF:**

Peso = Frecuencia × Bits × Canales × Segundos

Ejemplo del PDF:
P = 44100 × 16 × 2 × 3 × 60

Conversión usada en el PDF:
Peso(bits) / 8 = Peso(bytes)

---

# 🔌 STREAMING

## Cálculo de ancho de banda total (Unicast)
**Fórmula del PDF:**

BW(tot) = BW(stream) × N(usuarios)

---

# 🎥 VÍDEO

## Cálculo de peso (vídeo sin comprimir)
**Fórmula del PDF:**

Peso = (Ancho × Alto) × Profundidad de color × FPS × Tiempo

---

## Cálculo de peso (vídeo comprimido)
**Fórmula del PDF:**

Peso = Bitrate × Tiempo

---

# EJEMPLOS (convertidos a fórmula)

## Audio WAV (ejemplo del PDF)
P = 44100 × 16 × 2 × 3 × 60  
P / 8 = bytes  
bytes ≈ 31.75 MB

---

#  RESUMEN DE TODAS LAS FÓRMULAS DEL PDF

1. **Peso audio sin compresión:**  
   Peso = Frecuencia × Bits × Canales × Segundos

2. **Conversión bits → bytes:**  
   bytes = bits / 8

3. **Ancho de banda total en Unicast:**  
   BW(tot) = BW(stream) × N(usuarios)

4. **Peso vídeo sin comprimir:**  
   Peso = (Ancho × Alto) × Profundidad × FPS × Tiempo

5. **Peso vídeo comprimido:**  
   Peso = Bitrate × Tiempo

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
# Ejercicios de Cálculo – Streaming, Audio y Vídeo

Formato Markdown listo para GitHub
##  Cálculo de Peso – Audio
 Conversión de unidades usadas

    1 kHz=1000 Hz

    1 kbps=1000 bps

    1 Mbps=1 000 000 bps

    1 byte=8 bits

    1 MB=1 000 000 bytes

    1 GB=1 000 000 000 bytes
---

### 1. Peso WAV de 5 minutos (44.1 kHz, 16 bits, estéreo)
Conversión previa

    Frecuencia:
    44.1 kHz=44 100 Hz

    Tiempo:
    5 min=300 s

Cálculo
Peso(bits)=44100×16×2×300
44100×16=705600
705600×2=1411200
1411200×300=423360000 bits

Conversión a bytes:
4233600008=52920000 bytes

Conversión a MB:
52920000106≈52.92 MB
 Resultado: ~52.9 MB
 
---
### 2. Streaming MP3 128 kbps con 25 oyentes
Conversión previa
128 kbps=128 000 bps
Cálculo
128×25=3200 kbps
3200 kbps=3.2 Mbps
 Resultado: 3.2 Mbps de subida
 
---
### 3. Bitrate de audio 48 kHz, 24 bits, mono
Conversión previa
48 kHz=48 000 Hz
Cálculo
48000×24×1=1152000 bps
1152000 bps=1.152 Mbps
 Resultado: 1.152 Mbps
 
---
### 4. Servidor 10 Mbps → oyentes a 192 kbps
Conversión previa
10 Mbps=10 000 kbps
Cálculo
10000192≈52.08
 Resultado: 52 oyentes
 Cálculo de Peso – Vídeo
 Conversión de unidades usadas

    1 Gbps=1 000 000 000 bps

    1 TB=1 000 GB

    1 GB=8 000 000 000 bits
---
## Ejercicio 1 – RAW 4K, 60 fps, 30 bits
Datos

    Resolución:
    3840×2160=8 294 400 píxeles

    Profundidad: 30 bits

    FPS: 60

A. Bitrate en Gbps
8294400×30=248832000 bits/frame
248832000×60=14929920000 bps
14929920000109≈14.93 Gbps
 Resultado: ~14.9 Gbps
 
B. Tamaño de 10 segundos
14.93 Gbps×10=149.3 Gbit
Conversión a GB:
149.3×1098×109=18.66 GB
 Resultado: ~18.7 GB
 
C. Minutos que caben en 1 TB
Conversión previa
1 TB=1000 GB=8×1012 bits
Segundos=8×101214.93×109≈536 s
53660≈8.93 min
 Resultado: ~9 minutos
 
---
## Ejercicio 2 – Streaming YouTube 1080p
A. Porcentaje de uso de la línea
620=0.30=30%
 Resultado: 30% de la subida
B. Si 4 alumnos emiten a 6 Mbps
6×4=24 Mbps

La línea es de 20 Mbps → se supera.
Consecuencias técnicas:

    Buffering constante

    Aumento de latencia

    Pérdida de frames

    Congestión de red

 Resultado: la emisión se degrada o se corta
C. Solución técnica

Para que 4 alumnos emitan sin saturar:
Lıˊmite=20 Mbps

Si cada uno usa 4 Mbps:
4×4=16 Mbps
Soluciones válidas:

    Reducir bitrate a 4 Mbps

    Bajar resolución a 720p

    Usar codificación más eficiente (H.265)

    Emitir a través de un único encoder y redistribuir localmente
---
Resultado: bajar bitrate a 4 Mbps por alumno
## Preguntas finales – Simulación de Streaming
1. Almacenamiento: 500 GB → horas a 2 Mbps
Conversión previa
500 GB=4×1012 bits
Segundos=4×10122×106=2×106 s
Horas=2×1063600≈555.56
 Resultado: ~555 horas (~23 días)
2. Red: 100 Mbps → usuarios a 400 kbps (80% límite)
Conversión previa
80% de 100 Mbps=80 Mbps
400 kbps=0.4 Mbps
800.4=200
 Resultado: 200 usuarios simultáneos

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
## 13. Conversion
#  Tabla completa de conversiones (Audio, Vídeo, Red, Almacenamiento y Tiempo)

##  AUDIO

### Frecuencia
1 Hz  = 1 ciclo/segundo  
1 kHz = 1.000 Hz  
1 MHz = 1.000.000 Hz  

### Profundidad de bits
16 bits = 2 bytes  
24 bits = 3 bytes  
32 bits = 4 bytes  

### Canales
Mono   = 1 canal  
Estéreo = 2 canales  

---

##  RED (BITRATE)

### Bits y bytes
1 byte = 8 bits  
1 kilobyte (KB) = 1.000 bytes  
1 megabyte (MB) = 1.000.000 bytes  
1 gigabyte (GB) = 1.000.000.000 bytes  

### Bitrate
1 bps  = 1 bit/segundo  
1 kbps = 1.000 bps  
1 Mbps = 1.000.000 bps  
1 Gbps = 1.000.000.000 bps  

### Conversión rápida
- De kbps a Mbps:  
  Mbps = kbps / 1000  
- De Mbps a kbps:  
  kbps = Mbps × 1000  
- De bps a bytes/s:  
  bytes/s = bps / 8  

---

##  ALMACENAMIENTO

### Bytes
1 KB = 1.000 bytes  
1 MB = 1.000.000 bytes  
1 GB = 1.000.000.000 bytes  
1 TB = 1.000 GB = 1.000.000.000.000 bytes  

### Bits
1 byte = 8 bits  
1 KB = 8.000 bits  
1 MB = 8.000.000 bits  
1 GB = 8.000.000.000 bits  
1 TB = 8.000.000.000.000 bits  

---

##  VÍDEO

### Resoluciones típicas
- 240p  = 426 × 240  
- 480p  = 854 × 480  
- 720p  = 1280 × 720  
- 1080p = 1920 × 1080  
- 4K    = 3840 × 2160  
- 8K    = 7680 × 4320  

### Profundidad de color
8 bits  = 256 niveles por canal  
10 bits = 1024 niveles por canal  
12 bits = 4096 niveles por canal  
24 bits = 8+8+8 (RGB estándar)  
30 bits = 10+10+10 (HDR)  

### FPS
1 fps = 1 frame por segundo  
60 fps = 60 frames por segundo  

---

##  TIEMPO

1 minuto = 60 segundos  
1 hora   = 3600 segundos  
1 día    = 24 horas = 86.400 segundos  

---

##  FORMULAS DE CONVERSIÓN USADAS EN LOS EJERCICIOS

### Audio sin comprimir (WAV)
Peso(bits) = Frecuencia × Bits × Canales × Segundos  
Peso(bytes) = Peso(bits) / 8  
Peso(MB) = Peso(bytes) / 1.000.000  

### Bitrate de audio PCM
Bitrate(bps) = Frecuencia × Bits × Canales  

### Streaming
BW_total = Bitrate × Número_de_oyentes  

### Vídeo RAW sin comprimir
Bits_por_frame = (Ancho × Alto) × Profundidad  
Bitrate = Bits_por_frame × FPS  
Tamaño = Bitrate × Tiempo  

### Vídeo comprimido
Peso = Bitrate × Tiempo  

### Capacidad de almacenamiento
Segundos = Bits_totales / Bitrate  
Horas = Segundos / 3600  

### Capacidad de red
Usuarios = Ancho_de_banda_total / Bitrate_por_usuario  


---
## 14. Conclusión

A lo largo de esta unidad se han aprendido los conceptos básicos del streaming, los protocolos más utilizados y el funcionamiento de servidores de audio y vídeo.  
Las prácticas han permitido trabajar con herramientas reales como Icecast, Mixxx y FFmpeg.


