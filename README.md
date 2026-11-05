# ppp-2025-05-acelerografo-esp32-eagle

> **Red Sísmica del Austro (RSA) — Universidad de Cuenca**  
> Prácticas Preprofesionales (PPP) • Diseño de Hardware Electrónico, CAD/EDA (Autodesk EAGLE) e Instrumentación Sísmica

---

## 📋 Ficha Técnica del Proyecto

| Campo | Detalle |
| :--- | :--- |
| **Código Institucional** | `RSA-PPP-2025-05` |
| **Nombre del Proyecto** | Sistema de Registro Continuo de Señales Acelerométricas basado en ESP32 (Hardware Electrónico y PCBs) |
| **Practicante** | Christian Daniel Loja Chalco (`christian.loja@ucuenca.edu.ec`) |
| **Carrera / Institución** | Ingeniería en Telecomunicaciones — Universidad de Cuenca |
| **Tutor Institucional** | Ing. Milton Muñoz (`milton.munozc@ucuenca.edu.ec`) — RSA |
| **Duración / Horas** | 96 horas intensivas (3 semanas) • Presencial |
| **Fecha de Ejecución** | 2025-02-10 al 2025-03-03 |
| **Estado** | `Culminado` |

---

## 🏛️ Contexto Institucional y Trazabilidad Técnica

Este repositorio constituye el eslabón de hardware central dentro de la **trilogía institucional de desarrollo del Acelerógrafo ESP32** en la Red Sísmica del Austro:

```text
+-------------------------------------------------------------------------------+
|                      TRILOGÍA DEL ACELERÓGRAFO ESP32 (RSA)                    |
+-------------------------------------------------------------------------------+
|                                                                               |
|  1. Firmware y Telemetría IoT (2024):                                         |
|     -> ppp-2024-04-acelerografo-esp32-firmware (Jorge Zhangallimbay)          |
|        Validación experimental en protoboard, FreeRTOS, muestreo ADXL355 a    |
|        250 Hz, sincronía GPS/RTC, almacenamiento MicroSD y protocolo MQTT.   |
|                                                                               |
|  2. Diseño de Hardware y PCBs en Autodesk EAGLE (2025) [ESTE REPOSITORIO]:     |
|     -> ppp-2025-05-acelerografo-esp32-eagle (Christian Daniel Loja)           |
|        Diseño de dos tarjetas de circuito impreso para el circuito previo:    |
|        - Versión Modular: Tarjeta base con zócalos para módulos comerciales.  |
|        - Versión SMD: Placa compacta de alta densidad con componentes chip.   |
|                                                                               |
|  3. Migración a KiCad 10 y Estandarización PCBA (2026):                       |
|     -> ppp-2026-08-acelerografo-eagle-kicad (Edgar Joel Suárez)               |
|        Reconstrucción a KiCad 10 a partir de las imágenes y BOMs de este      |
|        repositorio, auditoría de pines hardware-firmware y manufactura JLCPCB.|
|                                                                               |
+-------------------------------------------------------------------------------+
```

> [!IMPORTANT]
> **Nota de Integridad de Artefactos y Memoria Técnica:**  
> Durante el desarrollo de esta práctica, los archivos fuente nativos de Autodesk EAGLE (`.sch` y `.brd`) no fueron incorporados a los commits originales y se extraviaron.  
> No obstante, este repositorio unificado resguarda con total fidelidad **la memoria técnica completa del trabajo**:
> * Paquetes completos de fabricación industrial `cam_outputs/` (Gerber RS-274X, taladrado Excellon Drill, archivos ODB++, listas de materiales `BOM_Assembly` y PDFs de planos).
> * Capturas en alta resolución de los esquemas por bloques funcionales (`images_schematic/`) y reportes de consistencia eléctrica (ERC).
> * Planos de ruteo Top/Bottom (`images_pcb_layers/`) y reportes de reglas de diseño (DRC).
> * Vistas y renderizados 3D de ensamble (`images_pcb_3d_view/`).
> 
> Estos elementos sirvieron como especificación técnica directa para la posterior migración exitosa a KiCad 10 en [ppp-2026-08-acelerografo-eagle-kicad](https://github.com/RSA-PPP/ppp-2026-08-acelerografo-eagle-kicad).

---

## 🎯 Descripción General y Objetivos

El propósito de esta práctica fue sustituir el prototipo de laboratorio montado sobre protoboard por circuitos impresos dedicados, eliminando falsos contactos, asegurando planos de masa continuos para mitigar el ruido en la lectura de aceleraciones y reduciendo el factor de forma para su futuro confinamiento en gabinetes estancos de campo.

### Objetivos Clave
1. **[Investigación y Arquitectura Modular]:** Relevar la interconexión de buses (SPI, UART, I2C) y seleccionar los módulos compatibles.
2. **[Esquemático Modular en EAGLE]:** Capturar el esquema eléctrico unificado con huellas para conectores y verificación ERC.
3. **[Layout y Ruteo de PCB Modular]:** Rutar pistas de alimentación y señales rápidas con headers de prueba y validación DRC.
4. **[Salidas de Manufactura y BOM Modular]:** Exportar paquete Gerber RS-274X, archivos Drill y lista de materiales modular.
5. **[Selección de Componentes SMD]:** Investigar y seleccionar integrados equivalentes (SoC ESP32, ADXL355 LGA-14, RTC SOIC-16, LDOs).
6. **[Esquemático SMD en EAGLE]:** Rediseñar el esquema con desacoplos de bajo ruido, protecciones ESD y verificación ERC.
7. **[Layout y Ruteo PCB SMD Compacta]:** Rutar la tarjeta en doble cara con planos de masa continuos (GND pour) y costura de vías (*via stitching*).
8. **[Documentación Técnica y Cierre]:** Generar paquetes de manufactura industrial y documentación técnica unificada.

> 📄 Para consultar el cronograma detallado de 96 horas y los checkpoints verificables, revisa el [Plan de Trabajo Oficial](docs/planificacion.md).

---

## 📂 Estructura del Repositorio Fusionado

El repositorio organiza de forma independiente y aislada las dos variantes desarrolladas por el practicante:

```text
ppp-2025-05-acelerografo-esp32-eagle/
│
├── docs/                                          # Documentación rectora y gobernanza PPP
│   └── planificacion.md                           # Plan de trabajo oficial rector (96 horas) y fases
│
├── modular/                                       # Etapa 1: Placa Modular basada en Breakouts
│   ├── cam_outputs/                               # Paquete de fabricación CAM (Gerbers, Drill, ODB++)
│   │   ├── BOM_Assembly/                          # Lista de materiales y posiciones PnP
│   │   ├── DrillFiles/                            # Archivos de perforación NC Drill
│   │   ├── GerberFiles/                           # Capas Gerber RS-274X (cobre, máscaras, serigrafía)
│   │   ├── ODBFiles/                              # Archivos ODB++
│   │   └── Gerber_images.pdf                      # Planos e imágenes de capas Gerber en PDF
│   ├── images_schematic/                          # Capturas de esquemáticos por bloques y reporte ERC
│   ├── images_pcb_layers/                         # Ruteo de capas Top/Bottom y reporte DRC
│   ├── images_pcb_3d_view/                        # Renderizados 3D de ensamble de la placa modular
│   └── README.md                                  # Ficha técnica y conexionado modular original
│
├── smd/                                           # Etapa 2: Placa Compacta de Montaje Superficial (SMD)
│   ├── cam_outputs/                               # Paquete de fabricación CAM industrial
│   │   ├── BOM_Assembly/                          # Lista de materiales SMD y posiciones PnP
│   │   ├── DrillFiles/                            # Archivos de perforación NC Drill
│   │   ├── GerberFiles/                           # Capas Gerber industriales
│   │   ├── ODBFiles/                              # Archivos ODB++
│   │   └── Gerber_images.pdf                      # Planos e imágenes de capas Gerber en PDF
│   ├── images_schematic/                          # Capturas de esquemáticos SMD y reporte ERC
│   ├── images_pcb_layers/                         # Ruteo de pistas, planos GND y reporte DRC
│   ├── images_pcb_3d_view/                        # Renderizados 3D de ensamble de la placa SMD
│   └── README.md                                  # Ficha técnica y componentes SMD original
│
├── README.md                                      # Este documento
├── LICENSE                                        # Licencia MIT
└── .gitignore                                     # Exclusiones de Git estándar y para Autodesk EAGLE
```

---

## ⚙️ Especificación de las Dos Variantes de Hardware

### 1. Versión Modular (`modular/`)
Diseñada como plataforma intermedia de laboratorio para pruebas, validación de señales y diagnóstico:
* **Procesamiento:** Socket para módulo comercial **ESP32 DevKit V1** (30 pines).
* **Sensores y Periféricos:** Zócalos hembra tipo peineta para acelerómetro **ADXL355 breakout**, módulo GPS **FGPMMOPA6H**, RTC **DS3231** y lector MicroSD estándar.
* **Alimentación:** Conector para convertidor reductor conmutado Buck DC-DC (MH-MINI-360) para entrada de 12V a 5V, y regulador lineal LD33V a 3.3V.
* **Depuración:** Cabeceras de pines de prueba (*test points*) en rieles de alimentación y líneas SPI/I2C para sondas de osciloscopio.
* 📄 Documentación detallada en: [`modular/README.md`](modular/README.md).

### 2. Versión de Montaje Superficial - SMD (`smd/`)
Diseñada para producción compacta y minimización de ruido electromagnético:
* **SoC Integrado:** **ESP32-WROOM-32E** soldado directamente sobre la placa con la antena de RF orientada hacia el borde libre de cobre.
* **Integrados de Soporte:** RTC **DS3231** (SOIC-16), convertidor Buck conmutado **MP2307** integrado en placa, conversor USB-UART **CH340G** con conector USB-C, y buffer triestado **74LVC125A** para aislamiento del bus SPI de la MicroSD.
* **Integridad de Señal:** Planos de masa continuos de cobre en ambas capas (*Top* y *Bottom* GND pour) con costura de vías (*via stitching*), condensadores de desacoplo cerámicos adyacentes a pines VCC y puntos de prueba SMD.
* 📄 Documentación detallada en: [`smd/README.md`](smd/README.md).

---

## 🛡️ Reglas de Trabajo y Control de Versiones

1. **Rama Principal:** La rama activa de trabajo es **`main`**.
2. **Formato de Commits:** Convención estándar en minúsculas:
   - `feat: [incorporación de módulo, capa o salida de manufactura]`
   - `fix: [corrección de netlist, huella o regla DRC]`
   - `docs: [actualización de documentación, esquemas o bitácora]`
3. **Control de Hitos por Git Tags:**
   - Hito de entrega técnica: `v1.0.0`.

---

## 📞 Contacto y Soporte Institucional

* **Practicante:** Christian Daniel Loja Chalco (`christian.loja@ucuenca.edu.ec`)
* **Tutor Institucional:** Ing. Milton Muñoz (`milton.munozc@ucuenca.edu.ec`)
* **Institución:** [Red Sísmica del Austro (RSA)](https://redsismicaaustro.github.io/RSA-Metodologias) — Universidad de Cuenca
