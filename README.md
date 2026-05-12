# ESP32 Multi-Protocol Gateway
### Wi-Fi 6 · BLE · LTE · LoRa · GPS

Repositorio del diseño electrónico de un **gateway IoT multiprotocolo** basado en ESP32. El proyecto integra conectividad inalámbrica local y de largo alcance mediante Wi-Fi/BLE, comunicación celular LTE, enlace LoRa y recepción GPS/GNSS, con el objetivo de servir como plataforma para aplicaciones de telemetría, monitoreo remoto, rastreo y comunicación entre dispositivos IoT.

---

## Descripción general

Este proyecto consiste en el diseño de una PCB personalizada para un gateway multiprotocolo. El sistema está pensado para recibir, procesar y retransmitir datos provenientes de sensores o nodos remotos utilizando distintos medios de comunicación.

El diseño incluye bloques de alimentación, protección, comunicación USB/UART, microcontrolador principal, módulo LTE/GNSS, interfaz LoRa, conectores de antena, tarjeta SIM y archivos de fabricación necesarios para revisión o producción del PCB.

---

## Características principales

- Controlador principal basado en familia **ESP32**.
- Soporte para comunicación **Wi-Fi 6** y **Bluetooth Low Energy (BLE)**, según el módulo ESP32 utilizado.
- Comunicación celular mediante módulo **LTE**.
- Recepción de posicionamiento mediante **GPS/GNSS**.
- Comunicación de largo alcance mediante **LoRa**.
- Interfaz **USB Type-C** para alimentación, programación y comunicación UART.
- Circuito de batería y administración de energía.
- Regulación de voltajes para los bloques de 4.2 V, 3.3 V y alimentación del módem.
- Interfaz para **tarjeta SIM**.
- Conectores de antena para LTE, GNSS y LoRa.
- Archivos de diseño, documentación y fabricación incluidos.

---

## Aplicaciones posibles

Este gateway puede utilizarse como base para:

- Sistemas de telemetría IoT.
- Monitoreo remoto de sensores.
- Rastreo de activos mediante GPS/GNSS.
- Enlace entre redes LoRa y servicios en la nube.
- Prototipos de comunicación M2M.
- Sistemas embebidos con conectividad celular.
- Gateways para zonas con baja cobertura Wi-Fi.

---

## Arquitectura del sistema

```text
                 +--------------------+
                 |   Antena LoRa      |
                 +---------+----------+
                           |
+-------------+    +-------v-------+
| USB Type-C  |--->|  ESP32 Core   |<---- Wi-Fi / BLE
| CP2104 UART |    +-------+-------+
+-------------+            |
                           | UART / GPIO / Control
                    +------v-------+
                    | Level Shifter|
                    +------+-------+
                           |
                    +------v-------+
                    |  LTE / GNSS  |----> Antenas LTE/GNSS
                    |  SIM7600     |
                    +------+-------+
                           |
                    +------v-------+
                    |   SIM Card   |
                    +--------------+

+----------------------------------------+
| Battery / Charger / Regulators / Power |
+----------------------------------------+
```

---

## Bloques funcionales del hardware

### 1. Núcleo ESP32

El ESP32 funciona como unidad principal de procesamiento y control. Desde este bloque se gestionan las interfaces de comunicación, señales de control, buses digitales y comunicación con los módulos externos.

### 2. Comunicación USB/UART

El diseño incluye una interfaz USB Type-C y conversor USB-UART para programación, depuración y comunicación serial con el microcontrolador.

### 3. Módem LTE/GNSS

El bloque LTE permite comunicación celular para transmisión de datos en zonas donde no exista conectividad Wi-Fi. También se incluye la interfaz GNSS/GPS para aplicaciones de posicionamiento.

### 4. Interfaz LoRa

El módulo LoRa permite comunicación inalámbrica de largo alcance y bajo consumo, útil para redes de sensores o comunicación entre nodos IoT.

### 5. Administración de energía

El sistema integra etapas de regulación y protección para alimentar correctamente los diferentes bloques del circuito, incluyendo alimentación por USB, batería y voltajes requeridos por el módem y el controlador principal.

### 6. Antenas y RF

El diseño contempla conectores de antena para las interfaces inalámbricas. Las señales RF deben mantenerse lo más cortas posible, con plano de tierra adecuado y respetando las reglas de impedancia correspondientes.

---

## Archivos incluidos en el repositorio

```text
ESP32-Multi-Protocol-Gateway-WiFi-6-BLE-LTE-LoRa-GPS-
|
├── README.md
├── GATEWAY MULTIPROTOCOL.DSN
├── gateway multiprotocol.brd
├── SCHEMATIC GATEWAY MULTIPROTOCOL.pdf
├── gateway multiprotocol brd.pdf
├── GATEWAY MULTIPROTOCOL.BOM
|
├── TOP.art
├── BOTTOM.art
├── GND.art
├── POWER.art
└── EXTRA_VIAS.art
```

### Descripción de archivos

| Archivo | Descripción |
|---|---|
| `GATEWAY MULTIPROTOCOL.DSN` | Archivo del esquemático en OrCAD Capture. |
| `gateway multiprotocol.brd` | Archivo principal del PCB en Cadence Allegro PCB Editor. |
| `SCHEMATIC GATEWAY MULTIPROTOCOL.pdf` | Versión PDF del esquemático. |
| `gateway multiprotocol brd.pdf` | Vista o documentación PDF del diseño PCB. |
| `GATEWAY MULTIPROTOCOL.BOM` | Lista de materiales del proyecto. |
| `TOP.art` | Archivo de fabricación/artwork de la capa superior. |
| `BOTTOM.art` | Archivo de fabricación/artwork de la capa inferior. |
| `GND.art` | Archivo de fabricación/artwork asociado a plano o capa de tierra. |
| `POWER.art` | Archivo de fabricación/artwork asociado a alimentación. |
| `EXTRA_VIAS.art` | Archivo adicional de vías/artwork del diseño. |

---

## Herramientas utilizadas

- **OrCAD Capture** para diseño esquemático.
- **Cadence Allegro PCB Editor** para layout y diseño del PCB.
- Generación de archivos de fabricación mediante **Artwork/Gerber**.
- Generación de BOM desde el entorno de diseño electrónico.

---

## Flujo básico de uso del proyecto

### 1. Revisar el esquemático

Abrir el archivo:

```text
GATEWAY MULTIPROTOCOL.DSN
```

o consultar directamente:

```text
SCHEMATIC GATEWAY MULTIPROTOCOL.pdf
```

### 2. Revisar el PCB

Abrir en Allegro PCB Editor:

```text
gateway multiprotocol.brd
```

o consultar el PDF:

```text
gateway multiprotocol brd.pdf
```

### 3. Revisar la lista de materiales

Consultar:

```text
GATEWAY MULTIPROTOCOL.BOM
```

Este archivo contiene los componentes utilizados en el diseño, sus referencias y datos necesarios para revisión o ensamble.

### 4. Revisar archivos de fabricación

Los archivos `.art` corresponden a salidas de fabricación/artwork generadas desde Allegro. Antes de fabricar, se recomienda validarlos en un visor Gerber compatible.

---

## Recomendaciones antes de fabricación

Antes de enviar el PCB a producción, se recomienda verificar:

- Reglas DRC del diseño.
- Separación mínima entre pistas y pads.
- Anchos de pista para alimentación.
- Integridad del plano de tierra.
- Ruteo de señales RF.
- Ruteo del par USB D+ / D-.
- Orientación de conectores y módulos.
- Footprints de componentes críticos.
- Polaridad de diodos, capacitores y conectores.
- Archivos de taladro o **NC Drill**, si aplican.
- Correspondencia entre BOM, esquemático y PCB.

---

## Consideraciones de diseño

### Señales RF

Las líneas de antena para LTE, GNSS y LoRa deben mantenerse cortas, directas y con referencia de tierra continua. Es importante evitar pasar señales digitales rápidas o fuentes switching cerca de las rutas RF.

### Alimentación del módem LTE

El módem celular puede demandar picos de corriente altos durante transmisión. Por ello, los capacitores de reserva y las pistas de alimentación deben dimensionarse correctamente.

### USB

El par diferencial USB D+ y D- debe rutearse de forma paralela, con longitud similar y evitando cambios bruscos de dirección.

### Reguladores switching

Los reguladores conmutados deben mantener loops de corriente compactos. Los inductores, capacitores de entrada/salida y resistencias de feedback deben colocarse cerca del integrado correspondiente.

---

## Estado del proyecto

El repositorio contiene el diseño de hardware y archivos asociados para revisión, documentación y fabricación del PCB. El enfoque actual del repositorio es el diseño electrónico; el firmware de aplicación puede desarrollarse como una etapa posterior.

---

## Autor

Proyecto desarrollado por **mcospin88** como diseño académico de un gateway IoT multiprotocolo.

---

## Licencia

Este proyecto se presenta con fines académicos y de documentación técnica. Para uso comercial, fabricación en volumen o redistribución, se recomienda agregar una licencia formal al repositorio.

---

## Nota

Este diseño debe ser validado eléctricamente antes de una fabricación definitiva. Se recomienda realizar una revisión técnica completa del esquemático, PCB, BOM y archivos Gerber/artwork antes de enviar el proyecto a producción.
