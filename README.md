# Redes
# 📡 Servicios de Streaming
## Memoria – Servicios en Red  
### 2º ASIX

---

**Alumno:** Nombre Apellidos  
**Asignatura:** Servicios en Red  
**Curso:** 2024 / 2025  
**Centro:** ____________________  

---

## 📚 Índice

1. Introducción  
2. Descarga directa vs Streaming  
3. Topologías de red  
4. TCP vs UDP  
5. Calidad de Servicio (QoS)  
6. Protocolos de Streaming  
7. Icecast2  
8. Códecs de audio  
9. Ejercicios de audio  
10. Vídeo digital  
11. Ejercicios de vídeo  
12. Prácticas paso a paso  
13. Conclusión  

---

## 1. Introducción

El streaming es una forma de transmitir audio o vídeo a través de una red para que el usuario pueda reproducirlo en el momento, sin necesidad de descargar el archivo completo.  
Hoy en día se utiliza en plataformas como Spotify, YouTube, Twitch o Netflix.

---

## 2. Descarga directa vs Streaming

### Descarga directa
- El usuario descarga un archivo completo.
- El servidor envía todo el fichero aunque no se reproduzca entero.
- Consume más ancho de banda.
- Ejemplo típico: descargar una canción o un vídeo.

### Streaming
- Los datos se envían poco a poco en forma de flujo.
- No se guarda el archivo completo en el dispositivo.
- Solo se usa el ancho de banda necesario.
- Ejemplo: escuchar radio online o ver un vídeo en YouTube.

---

## 3. Topologías de red

### Unicast
- Conexión directa entre servidor y cada usuario.
- El servidor envía el mismo stream a cada oyente.
- No es muy escalable cuando hay muchos usuarios.

### Multicast
- El servidor envía un único stream.
- Los routers se encargan de repartirlo.
- Solo se usa en redes internas.

---

## 4. TCP vs UDP

### TCP
- Es un protocolo fiable.
- Si se pierde un paquete, se vuelve a enviar.
- Tiene más latencia.
- Es el más usado en streaming comercial.

### UDP
- No garantiza que lleguen todos los paquetes.
- Tiene muy poca latencia.
- Se usa cuando es importante el tiempo real.

---

## 5. Calidad de Servicio (QoS)

### Jitter
Es la variación en el tiempo de llegada de los paquetes.  
Si es muy alto, el audio o el vídeo puede cortarse.

### Buffer
Es una memoria temporal donde se guardan datos antes de reproducirse.
- Más buffer = más estabilidad.
- Más buffer = más retraso.

### Burst-on-Connect
Al conectarse un oyente, el servidor envía datos más rápido al inicio para que el audio empiece a sonar antes.

---

## 6. Protocolos de Streaming

### HTTP Legacy
- Usa TCP.
- Flujo continuo de datos.
- Se usa en radios online como Icecast.

### HTTP Adaptativo
- Divide el contenido en pequeños fragmentos.
- Permite cambiar la calidad según la conexión.
- Usado por Netflix y YouTube.

### Real-Time
- RTMP: envío de vídeo al servidor.
- RTSP: cámaras IP.
- WebRTC: videollamadas.

---

## 7. Icecast2

Icecast2 es un servidor de streaming de audio de código abierto.

Características principales:
- Distribuye audio a muchos oyentes.
- No crea el contenido.
- Soporta MP3 y OGG.
- Usa puntos de montaje como `/radio`.

---

## 8. Códecs de audio

Un códec sirve para comprimir y descomprimir audio.

Parámetros importantes:
- Frecuencia de muestreo.
- Profundidad de bits.
- Número de canales.

Tipos de códecs:
- Con pérdida: MP3.
- Sin pérdida: WAV, FLAC.

---

## 9. Ejercicios de audio

En este apartado se realizan ejercicios sobre:
- Cálculo del tamaño de archivos de audio.
- Consumo de ancho de banda en streaming.
- Cálculo de bitrate.
- Número máximo de oyentes.

(Los cálculos se han realizado siguiendo las fórmulas vistas en clase.)

---

## 10. Vídeo digital

El vídeo digital funciona de forma parecida al audio, pero incluye imagen.

Conceptos importantes:
- Resolución (1080p, 4K).
- FPS (fotogramas por segundo).
- Bitrate.
- Contenedor (MP4, MKV).

---

## 11. Ejercicios de vídeo

En estos ejercicios se trabaja con:
- Cálculo de bitrate de vídeo sin comprimir.
- Espacio necesario en disco.
- Uso del ancho de banda en emisiones en directo.

(Los resultados se obtienen aplicando las fórmulas explicadas en clase.)

---

## 12. Prácticas paso a paso

### Práctica 1: Radio Online con Icecast2 y Mixxx

#### Servidor de streaming
1. Crear una máquina virtual con Ubuntu 24.
2. Configurar la red en adaptador puente.
3. Comprobar que el sistema tiene sonido.
4. Actualizar el sistema:
