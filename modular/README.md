# 🚀 PCB para Monitoreo de Señales Acelerométricas en Red de Control Sísmico  

## 📌 Introducción  

Este proyecto consiste en el diseño de una placa PCB con componentes y sensores modulares para la adquisición y transmisión de señales acelerométricas, destinada a redes de control sísmico. La placa integra un microcontrolador **ESP32** para procesamiento y comunicación inalámbrica, junto con componentes electrónicos y sensores optimizados para garantizar precisión en la medición de vibraciones. Los dispositivos utilizan comunicación **SPI**, **I2C** y **UART**, protocolos ampliamente empleados en electrónica para la transferencia de datos entre microcontroladores, sensores, memorias, etc. 

### Conexiones clave:  
- **SPI**:  
  - `SCLK` (Reloj), `MOSI` (Master Out Slave In), `MISO` (Master In Slave Out), `SS/CS` (Selección de esclavo).  
- **I2C**:  
  - `SCL` (Reloj), `SDA` (Datos).  
- **UART**:  
  - `TX` (Transmisión), `RX` (Recepción). 

### Implementación en el proyecto:  
- **GPS**: Comunicación UART.  
- **Acelerómetro ADXL355Z**: Comunicación SPI.  
- **RTC-DS3231**: Comunicación I2C.  
- **Tarjeta µSD**: Comunicación SPI.  
- **USB del ESP32-DEVKIT**: Protocolo UART. 

### Alimentación:  
Todos los dispositivos operan a **+3.3V**, obtenidos mediante:  
1. **Buck-Converter** (+12V a +5V).  
2. **Regulador LD33V** (+5V a +3.3V). 

🔗 Este proyecto se basa en la electrónica (hardware) necesaria para que el sistema de monitoreo sísmico funcione, todo el software que usa este proyecto se encuentra en el repositorio [RSA Sensor](https://github.com/JorgeZh-hub/RSA_sensor)

---

## 🔍 Componentes Utilizados  
A continuación se detallan los componentes clave del diseño:  

### 🎛️ Microcontrolador  
- **ESP32-DEVKITC-32D** (Microcontrolador base: `ESP32-WROOM-32E`).  

### 📊 Sensores, Módulos y Reloj
- **Acelerómetro** (Modelo: `ADXL355Z` o equivalente, Tipo: `Modular`).
- **GPS** (Modelo: `GPS-FPGMMOPA6H` o equivalente, Tipo: `Modular`).
- **RTC** (Modelo: `RTC-DS3231` o equivalente, Tipo: `Modular`).
- **Buck-Converter** (Modelo: `MH-MINI-360` o equivalente, Tipo: `Modular`).
- **Lector µSD** (Modelo: Genérico, Tipo: `Modular`).

### 🔧 Circuitos Integrados (ICs)  
- **LD33V** (Regulador de voltaje, Tipo: `SMD SOT-223`) o equivalente. 

#### Capacitores  
- `C1`: 100nF (Tipo: `Cerámico Modular 2.54mm`, Código: `104`).
- `C2`: 10µF (Tipo: `Electrolítico Modular 5mm`).
- `C3`: 10µF (Tipo: `Electrolítico Modular 5mm`).
- `C4`: 100nF (Tipo: `Cerámico Modular 2.54mm`, Código: `104`).
- `C5`: 100µF (Tipo: `Electrolítico Modular 5mm`).
- `C6`: 100µF (Tipo: `Electrolítico Modular 5mm`).
- `C7`: 100nF (Tipo: `Cerámico Modular 2.54mm`, Código: `104`).

### 🔋 Conector de Fuente de Alimentación (+12V)  
- Conector XH 2 posiciones.  

### 📊 Test Points para Depuración  
- **LD33V**: `GND/VCC` (Pin Header 1x2).  
- **DS3231**: `SDA1/SCL1` (Pin Header 1x2).  
- **GPS**: `TXGPS/RXGPS` (Pin Header 1x2).  
- **Lector µSD**: `CS/SCK/MOSI/MISO` (Pin Header 1x4).  
- **ADXL355Z**: `IO15/IO13/IO12/IO14` (Pin Header 1x4).

---

## 🖼️ Imágenes del Diseño  

### Esquemático  
![Esquemático](/images_schematic)  

### Circuito Impreso  
![PCB](/images_PCB_layers)  

### Vista 3D de la PCB  
![Vista 3D de la PCB](/images_PCB_3D_view)  

---

## 📥 Descarga de Archivos Gerber, ODB, Drill y BOM
Los archivos para fabricación están disponibles en la carpeta [`/PCB_Modular`](/PCB_Modular) de este repositorio. Los archivos Gerber se pueden visualizar en el archivo PDF ![Gerber images](/PCB_Modular/CAMOutputs/Gerber_images.pdf).

---

## 🛠️ Características y Sustento del Diseño 
Este proyecto se ha llevado a cabo con el objetivo de optimizar el prototipo desarrollado sobre Protoboard para el sistema de monitoreo sísmico. Para ello, se han recopilado los componentes, en su mayoría modulares, necesarios para el proyecto.
El objetivo de esta placa es facilitar la depuración del sistema, reducir el tamaño del prototipo y mejorar la comunicación entre módulos mediante pistas de cobre con menor ruido. Adicionalmente, se busca implementar zonas de cobre y planos de masa para minimizar el ruido y las interferencias, así como mejorar la disipación térmica.
Se han colocado varios puntos de prueba (test points) para la depuración, utilizando peinetas (Pin Headers macho), en los que se pueden conectar jumpers o sondas de osciloscopio para observar las señales provenientes del módulo GPS, módulo RTC, acelerómetro, tarjeta µSD y los voltajes de alimentación que se dirigen al ESP32 y demás componentes.

En la etapa de alimentación, se ha implementado una fuente tipo Buck Converter, acompañada de un conjunto de capacitores implementados para filtrar el ruido de alta frecuencia y garantizar la estabilidad del voltaje de salida. Los capacitores utilizados son electrolíticos y cerámicos modulares, seleccionados tanto por su capacidad para mejorar la disipación de potencia como por la dificultad de encontrar los valores de capacitancia y voltaje requeridos en versión SMD, lo que hace necesario el uso de capacitores de tantalio.


### ✔️ Características Clave  
- **Reducción de tamaño**: Optimización del espacio en la PCB mediante la disposición eficiente de los módulos `ESP32DEV-KIT`, Buck-Converter `MH-Mini360`, Lector µSD y `RTC-DS3231`. La integración de estos componentes en una placa de circuito impreso proporciona una mayor resistencia a movimientos y vibraciones en comparación con sus versiones modulares en Protoboards.
- **Bajo ruido**: Para minimizar interferencias en las señales, se ha incorporado un plano de tierra en ambas caras del diseño, lo que permite cortocircuitar cualquier señal no deseada que pueda afectar la placa. Además, estos planos de tierra optimizan la disipación térmica de los componentes, contribuyendo a la reducción del ruido térmico.  
- **Comunicación inalámbrica**: Para mantener las funciones de conectividad Wifi se utilizó el DevKit de ESP32 con microcontrolador modelo `ESP32-WROOM-32E` cuyo encapsulado cuenta con una antena externa para la comunicación.  
- **Robustez y eficiencia energética**: Para garantizar la integridad de los componentes y un consumo energético eficiente, se ha implementado una fuente de voltaje basada en un Buck Converter, que reduce el voltaje de entrada de +12V a +5V. Posteriormente, este voltaje se convierte a +3.3V mediante un regulador `LD33V`, proporcionando la alimentación a todo el sistema. La fuente de alimentación principal se ha diseñado con un Buck Converter, ya que permite manejar corrientes considerables con una baja generación de calor y, sobre todo, por su alta eficiencia energética, que alcanza aproximadamente el 85%.

  
### 📐 Criterios de Diseño  
- **Grosor de líneas de alimentación**: Para una corriente de `1A` se recomienda `1mm` de ancho de pista, por lo tanto, dependiendo de la ubicación de la pista se usarán grosores dentro del rango `0.5–1mm` ya que las corrientes que circulan por la placa están por debajo de 1A.  
- **Grosor de líneas de transmisión**: Para comunicación SPI se recomiendan grosores de pista dentro del rango `0.2–0.3mm`. Para comunicación I2C se recomienda el rango `0.15–0.25mm`. Para comunicación UART se recomienda el rango `0.15–0.25mm`. Con el fin de mantener uniformidad en el diseño, se utilizará un grosor de `0.2032mm` para SPI, I2C y UART.
- **Diseño de doble cara**: Para optimizar la alimentación y conexión entre componentes, se ha diseñado una placa de doble cara. La cara superior alberga todos los componentes y la mayoría de las conexiones entre ellos, mientras que la cara inferior se emplea para transportar señales de comunicación SPI, I2C y UART que no pueden enrutarse en la capa superior. Este diseño permite la inclusión de un plano de tierra que cubre una gran parte de ambas caras, lo que contribuye significativamente a la reducción de interferencias.
- **Separación entre líneas de transmisión**: Para minimizar acoplamientos e interferencias en las señales SPI y UART, se recomienda una distancia entre pistas de al menos tres veces el ancho de la pista. De manera similar, para las señales I2C, se aconseja una separación mínima de dos veces el ancho de pista. Estos parámetros han sido aplicados en todos los enrutamientos de la placa.


---

## 🎯 Conclusiones y Recomendaciones  
### ✅ Verificación de errores eléctricos (ERC) y Verificación de reglas de diseño (DRC).
- La validación de reglas de diseño y de errores eléctricos realizada por el software Fusion 360 se muestra en una tabla que lista los errores encontrados. En este caso la validación de ERC y DRC muestran cero errores, estos resultados se muestran en las carpetas ![Esquemático](/images_schematic) y ![PCB](/images_PCB_layers) respectivamente.

### 🔍 Conclusiones  
- La placa ha sido diseñada en el Software Fusion 360 de AutoDesk. Esta plataforma facilita el desarrollo y diseño de circuitos gracias a la gran variedad de componentes recopilados en sus librerías. Sin embargo, durante la realización de este proyecto no se encontraron librerías que contengan sensores como el acelerómetro `ADXL355Z`, el módulo `GPS-FPGMMOPA6H`, el buck-converter `MH-MINI-360`, IC `LD33V`, el módulo `RTC-DS3231`, módulo Micro-SD y el `ESP32-DEVKITC-32D`. Por lo tanto, estos componentes tuvieron que ser diseñados por completo (esquemático, footprint y modelo 3D) en la misma plataforma Fusion 360. Varios paquetes de software de AutoDesk (incluido Fusion 360) son dirigidos hacia la comunidad científica y de investigación, por ende cuentan con licencias sin costo para estudiantes o miembros de universidades. Estas son opciones excelentes y completas para diseño electrónico, PCB, radiofrecuencia, mecánica y muchas otras áreas de ingeniería.
- Para simplificar el ensamblaje del diseño, se emplearon componentes ampliamente disponibles en el mercado. En el caso de los capacitores del circuito de alimentación, se optó por versiones modulares debido a su mayor capacidad de disipación de potencia en comparación con el resto del circuito. Además, algunos valores de capacitancia, como 10 µF y 100 µF, pueden ser difíciles de encontrar en formato SMD, lo que hizo necesario recurrir a estos componentes modulares.
- Los planos de tierra desempeñan un papel fundamental en la mejora de la disipación térmica y la reducción de interferencias, por lo que ambas caras del PCB han sido cubiertas casi en su totalidad con este plano. Aunque los planos de cobre —zonas de cobre aisladas de cualquier señal y distintas al plano de tierra— también contribuyen a la disipación térmica, en este caso no se han implementado, ya que podrían generar interferencias en las señales I2C, SPI y UART. Además, dado que los planos de tierra ocupan la mayor parte de los espacios vacíos del PCB, la incorporación de planos de cobre no resulta necesaria.
- A diferencia del prototipo desarrollado sobre un Protoboard, este diseño es significativamente más compacto, rígido y seguro, ya que las conexiones se realizan mediante pistas de cobre en lugar de jumpers o hileras del Protoboard. Esta mejora es crucial, ya que elimina el riesgo de desconexiones y falsos contactos, problemas comunes en proyectos implementados sobre un Protoboard.

### ⚠️ Precauciones  
- **Montaje**: Es fundamental verificar la polaridad de los componentes sensibles, como la entrada de 12 voltios y los capacitores electrolíticos. Para garantizar un ensamblaje seguro, se recomienda revisar los modelos 3D y los footprints antes y durante la instalación.
Además, durante el proceso de soldadura, es esencial aplicar el calor de manera controlada para evitar daños en la PCB o en los componentes. Por ello, se aconseja utilizar un cautín con temperatura regulable y una pistola de calor ajustable para un manejo preciso del calor.
- **Adquisición de componentes**: Es fundamental asegurarse de que los componentes a adquirir cuenten con un código SMD, una versión modular o un modelo compatible con cada elemento listado en el repositorio. De lo contrario, las diferencias en dimensiones podrían impedir su correcta soldadura en la PCB.  

### 🔮 Recomendaciones  
- Implementar una etapa de protección contra sobretensiones y picos de corriente para prevenir daños en el hardware y evitar pérdidas de información.  
- Considerar encapsulado/blindaje para ambientes hostiles.
- Incorporar un circuito de alimentación de respaldo para todo el sistema, ya que actualmente solo el RTC DS3231 cuenta con una batería que mantiene activo el reloj durante períodos de desconexión eléctrica.
- Soldar sockets sobre el PCB en lugar de fijar directamente los dispositivos, lo que previene daños por exceso de temperatura y permite la reutilización de los componentes en otros proyectos.
- Tras las pruebas con este diseño, se recomienda la implementación de la versión SMD del proyecto, disponible en [SMD-PCB-Design-for-Seismic-Monitoring](https://github.com/Christian-Loja/SMD-PCB-Design-for-Seismic-Monitoring)

---

## 📜 Licencia  
Este proyecto está bajo licencia **MIT**. Para más detalles, consulta el archivo [LICENSE](/LICENSE).  
