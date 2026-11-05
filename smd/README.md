# 🚀 PCB para Monitoreo de Señales Acelerométricas en Red de Control Sísmico  

## 📌 Introducción  
Este proyecto consiste en el diseño de una placa PCB (principalmente con componentes SMD) para la adquisición y transmisión de señales acelerométricas en redes de control sísmico. La placa integra un microcontrolador **ESP32** para procesamiento y comunicación inalámbrica, junto con componentes electrónicos y sensores optimizados para garantizar precisión en la medición de vibraciones. Los dispositivos utilizados usan comunicación SPI, I2C y UART. Estos tres protocolos son ampliamente utilizados en electrónica para la transferencia de datos entre dispositivos como microcontroladores, sensores, memorias, etc.

### Protocolos de Comunicación  
Los dispositivos utilizan tres protocolos estándar:  
- **SPI** (Serial Peripheral Interface):  
  - `SCLK` (Reloj), `MOSI` (Master Out Slave In), `MISO` (Master In Slave Out), `SS/CS` (Selección de esclavo)  
- **I2C** (Inter-Integrated Circuit):  
  - `SCL` (Reloj), `SDA` (Datos)  
- **UART** (Universal Asynchronous Receiver-Transmitter):  
  - `TX` (Transmisión), `RX` (Recepción)  

### Implementación  
- **GPS**: UART  
- **Acelerómetro ADXL355Z**: SPI  
- **RTC-DS3231**: I2C  
- **Tarjeta µSD**: SPI  
- **USB-C del ESP32**: UART  

### Alimentación  
El sistema opera a **+3.3V**, obtenido mediante:  
1. **Buck-Converter** (+12V a +5V)  
2. **Regulador LD33V** (+5V a +3.3V) 

🔗 Este proyecto se basa en la electrónica (hardware) necesaria para que el sistema de monitoreo sísmico funcione, todo el software que usa este proyecto se encuentra en el repositorio [RSA Sensor](https://github.com/JorgeZh-hub/RSA_sensor)

---

## 🔍 Componentes Utilizados  
A continuación se detallan los componentes clave del diseño:  

### 🎛️ Microcontrolador  
- **ESP32-WROOM-32** (Modelo: `ESP32-WROOM-32E`, Tipo: `SMD`).  

### 📊 Sensores, Módulos y Reloj
- **Acelerómetro** (Modelo: `ADXL355Z` o equivalente, Tipo: `Modular`).
- **GPS** (Modelo: `GPS-FPGMMOPA6H` o equivalente, Tipo: `Modular`).
- **RTC** (Modelo: `DS3231` o equivalente, Tipo: `SMD SOIC-16`).  

### 🔧 Circuitos Integrados (ICs)  
- **MP2307** (Tipo: `SMD SOIC8N (EXPOSED PAD)` o equivalente). 
- **LD33V** (Tipo: `SMD SOT-223` o equivalente). 
- **CH340G** (Tipo: `SMD SOP-16` o equivalente). 
- **74LVC125A** (Tipo: `SMD TSSOP−14` o equivalente). 

### 🔌 Componentes Pasivos  
#### Resistencias  
- `R1`: 8.2kΩ (Tipo: `SMD`, Componente SMD: `2512`).
- `R2`: 100kΩ (Tipo: `SMD`, Componente SMD: `2512`).
- `R3`: 8.2kΩ (Tipo: `SMD`, Componente SMD: `2512`).
- `R4`: 220kΩ (Tipo: `Potenciómetro Modular`, Componente: `PV36P`).
- `R5`: 3.3kΩ (Tipo: `SMD`, Componente SMD: `1206`).
- `R6`: 3.3kΩ (Tipo: `SMD`, Componente SMD: `1206`).
- `R7`: 3.3kΩ (Tipo: `SMD`, Componente SMD: `1206`).
- `R8`: 3.3kΩ (Tipo: `SMD`, Componente SMD: `1206`).
- `R9`: 4.7kΩ (Tipo: `SMD`, Componente SMD: `1206`).
- `R10`: 4.7kΩ (Tipo: `SMD`, Componente SMD: `1206`).
- `R11`: 4.7kΩ (Tipo: `SMD`, Componente SMD: `1206`).
- `R12`: 4.7kΩ (Tipo: `SMD`, Componente SMD: `1206`).
- `R13`: 200Ω (Tipo: `SMD`, Componente SMD: `1206`).
- `R14`: 5.11kΩ (Tipo: `SMD`, Componente SMD: `1206`).
- `R15`: 5.11kΩ (Tipo: `SMD`, Componente SMD: `1206`).
- `R16`: 4.7kΩ (Tipo: `SMD`, Componente SMD: `1206`).
- `R17`: 4.7kΩ (Tipo: `SMD`, Componente SMD: `2512`).
- `R18`: 10kΩ (Tipo: `SMD`, Componente SMD: `1206`).
- `R19`: 10kΩ (Tipo: `SMD`, Componente SMD: `1206`).

#### Capacitores  
- `C1`: 100nF (Tipo: `Cerámico Modular 2.54mm`, Código: `104`).
- `C2`: 10µF (Tipo: `Electrolítico Modular 5mm`).
- `C3`: 10µF (Tipo: `Electrolítico Modular 5mm`).
- `C4`: 200nF (Tipo: `Cerámico Modular 2.54mm`, Código: `204`).
- `C5`: 100µF (Tipo: `Electrolítico Modular 5mm`).
- `C6`: 100µF (Tipo: `Electrolítico Modular 5mm`).
- `C7`: 100nF (Tipo: `Cerámico Modular 2.54mm`, Código: `104`).
- `C8`: 12µF (Tipo: `Electrolítico Modular 5mm`).
- `C9`: 100nF (Tipo: `Cerámico Modular 2.54mm`, Código: `104`).
- `C10`: 4.7nF (Tipo: `Cerámico Modular 2.54mm`, Código: `402`).
- `C11`: 10nF (Tipo: `Cerámico Modular 2.54mm`, Código: `103`).
- `C12`: 12µF (Tipo: `Electrolítico Modular 5mm`).
- `C13`: 100nF (Tipo: `SMD`, Componente SMD: `0603`, Código: `104`).
- `C14`: 1µF (Tipo: `SMD`, Componente SMD: `0603`, Código: `105`).
- `C15`: 100nF (Tipo: `SMD`, Componente SMD: `0603`, Código: `104`).
- `C16`: 100nF (Tipo: `SMD`, Componente SMD: `0603`, Código: `104`).
- `C17`: 10µF (Tipo: `SMD`, Componente SMD: `1206`, Código: `106`).
- `C18`: 100nF (Tipo: `SMD`, Componente SMD: `0603`, Código: `104`).
- `C19`: 100nF (Tipo: `SMD`, Componente SMD: `0603`, Código: `104`).

#### Inductores  
- `L1`: 2uH (Tipo: `SMD`, Componente: `0805`).

#### Diodos  
- `D1`: Diodo `1N4148` (Encapsulado: `SMA/DO-214AC`, Código SMD: `US1M`).  
- `D2`: Diodo LED (Código SMD: `1206`).  
- `D3`: Diodo `1N4148` (Encapsulado: `SMA/DO-214AC`, Código SMD: `US1M`).  
- `D4`: Diodo `1N4148` (Encapsulado: `SMA/DO-214AC`, Código SMD: `US1M`).  
- `D5`: Diodo `1N4001` (Encapsulado: `SMA/DO-214AC`, Código SMD: `S1M`).  
- `D6`: Diodo `1N4001` (Encapsulado: `SMA/DO-214AC`, Código SMD: `S1M`).  
- `D7`: Diodo LED (Código SMD: `1206`).

#### Otros  
- Micro-SD Holder: (Tipo: Push in - Auto eject out (SMD/SMT), Modelo: `MSD-1-A`). (ACTUALIZACIÓN NECESARIA)
- Conector USB Tipo-C (3.1) Hembra: Componente: `12401832E402A`.

### 🔋 Conector de Fuente de Alimentación (+12V)  
- Conector XH 2 posiciones.  

### 📊 Test Points para Depuración  
- Pin Header 1x4 (Conectado al ADXL355Z): `IO15/IO13/IO12/IO14`
- Pin Header 1x5 (Conectado a 74LVC125A(Tarjeta SD), DS3231, CH340G(USB C), CH340G, DS3231): `MOSI/SCL/TXD0/RXD0/SDA`
- Pin Header 1x5 (Conectado a 74LVC125A(Tarjeta SD), 74LVC125A, 74LVC125A, GPS, GPS): `MISO/SCK/CS/RXGPS/TXGPS`

---

## 🖼️ Imágenes del Diseño  

### Esquemático  
![Esquemático](/images_schematic)  

### Circuito Impreso  
![PCB](/images_pcb_layers)  

### Vista 3D de la PCB  
![Vista 3D de la PCB](/images_pcb_3d_view)  

---

## 📥 Descarga de Archivos Gerber, ODB, Drill y BOM
Los archivos para fabricación están disponibles en la carpeta [`/PCB_SMD`](/PCB_SMD) de este repositorio. Los archivos Gerber se pueden visualizar en el archivo PDF ![Gerber images](/Gerber_images.pdf).

---

## 🛠️ Características y Sustento del Diseño 
Este proyecto se ha desarrollado con el objetivo de optimizar el prototipo modular del sistema de monitoreo sísmico, utilizando componentes de montaje superficial para mejorar la eficiencia y reducir el tamaño.
Además, se han implementado zonas de cobre y planos de masa para minimizar el ruido y las interferencias, así como mejorar la disipación térmica. Se han colocado varios puntos de prueba (test points) para la depuración, empleando peinetas (Pin Headers macho), en los cuales se pueden conectar jumpers o sondas de osciloscopio para monitorear las señales provenientes del módulo GPS, módulo RTC, acelerómetro, tarjeta micro SD y puerto USB-C, que se dirigen al ESP32. La versión modular de este proyecto se encuentra disponible en [Modular-PCB-Design-for-Seismic-Monitoring](https://github.com/Christian-Loja/Modular-PCB-Design-for-Seismic-Monitoring).

En la etapa de alimentación (Buck Converter), se han colocado resistores con código SMD `2512`, de mayor tamaño, para garantizar que soporten valores de potencia de hasta 0.5 watts. Asimismo, los capacitores utilizados son electrolíticos y cerámicos modulares, seleccionados por su capacidad para mejorar la disipación de potencia y porque los valores de capacitancia y voltaje requeridos son difíciles de encontrar en versión SMD, lo que hace necesario el uso de capacitores de tantalio.
El inductor también ha sido dimensionado para garantizar una operación dentro de un rango seguro; por esta razón, su encapsulado `0805` es ligeramente más grande que el de otros componentes SMD. Por otro lado, los componentes pasivos que operan con una alimentación de +3.3V presentan dimensiones más pequeñas (`0603` y `1206`), ya que manejan corrientes y voltajes más bajos. 

### ✔️ Características Clave  
- **Reducción de tamaño**: Optimización del espacio en la PCB mediante el reemplazo de los módulos ESP32DEV-KIT, Buck Converter MH-Mini360, Lector µSD y RTC-DS3231 por versiones SMD diseñadas específicamente para cada módulo. Para implementar estos reemplazos, fue necesario aplicar ingeniería inversa a los módulos originales. La adopción de versiones SMD no solo reduce el tamaño del diseño, sino que también mejora significativamente la resistencia a movimientos y vibraciones en comparación con sus equivalentes modulares. 
- **Bajo ruido**: Para minimizar las interferencias en las señales, se ha incorporado un plano de tierra en ambas caras del diseño, lo que permite cortocircuitar cualquier señal no deseada que pueda afectar la placa. Además, estos planos optimizan la disipación térmica de los componentes, contribuyendo a la reducción del ruido térmico.  
- **Comunicación inalámbrica**: Para mantener las funciones de conectividad Wifi del ESP32 se implementó el modelo ESP32-WROOM-32E cuyo encapsulado cuenta con una antena externa para la comunicación.  
- **Robustez y eficiencia energética**: Para garantizar la integridad de los componentes de la placa, se ha configurado una serie de diodos rectificadores que dirigen el flujo de corriente desde cualquiera de las fuentes de alimentación (+12V o USB-C) hacia un regulador de voltaje, encargado de suministrar los 3.3V requeridos por el sistema. La fuente de alimentación principal se ha implementado mediante un Buck Converter, ya que permite manejar corrientes considerables con una baja generación de calor y, principalmente, por su alta eficiencia energética, que alcanza aproximadamente el 85%.

### 📐 Criterios de Diseño  
- **Grosor de líneas de alimentación**: Para una corriente de `1A` se recomienda `1mm` de ancho de pista, por lo tanto, dependiendo de la ubicación de la pista se usarán grosores dentro del rango `0.5–1mm` ya que las corrientes que circulan por la placa están por debajo de 1A.  
- **Grosor de líneas de transmisión**: Para la comunicación SPI, se recomienda un grosor de pista dentro del rango de 0.2–0.3mm, mientras que para I2C y UART, el rango recomendado es de 0.15–0.25mm. Con el fin de mantener uniformidad en el diseño, se utilizará un grosor de 0.2032mm para las líneas de comunicación SPI, I2C y UART.
- **Diseño de doble cara**: Para optimizar la alimentación y la conexión entre los componentes, se ha diseñado una placa de doble cara. La cara superior alberga todos los componentes y la mayoría de las conexiones entre ellos, mientras que la cara inferior se utiliza para transportar señales de comunicación SPI, I2C y UART que no puedan enrutarse en la capa superior. El diseño de doble cara permite integrar un plano de tierra que cubre una gran parte de ambas caras, lo que contribuye significativamente a la reducción de interferencias.
- **Separación entre líneas de transmisión**: Para minimizar el acoplamiento e interferencias en las señales SPI y UART, se recomienda una distancia entre pistas de al menos tres veces el ancho de la pista. De manera similar, para las señales I2C, se aconseja una separación mínima de dos veces el ancho de pista. Estos parámetros han sido aplicados en todos los enrutamientos de la placa.

---

## 🎯 Conclusiones y Recomendaciones  
### ✅ Verificación de errores eléctricos (ERC) y Verificación de reglas de diseño (DRC).
- La validación de reglas de diseño y de errores eléctricos realizada por el software Fusion 360 se muestra en una tabla que lista los errores encontrados. En este caso la validación de ERC y DRC muestran cero errores, estos resultados se muestran en las carpetas ![Esquemático](/images_schematic) y ![PCB](/images_pcb_layers) respectivamente.

### 🔍 Conclusiones  
- La placa ha sido diseñada utilizando el software Fusion 360 de AutoDesk, una plataforma que facilita el desarrollo y diseño de circuitos gracias a su extensa biblioteca de componentes. Sin embargo, durante la realización de este proyecto, no se encontraron librerías que incluyeran sensores como el acelerómetro `ADXL355Z`, el módulo `GPS-FPGMMOPA6H`, `ESP32-WROOM-32E`, los circuitos integrados `MP2307`, `LD33V`, `CH340G`, `74LVC125A` y `DS3231`, así como el soporte para Micro-SD. Como resultado, fue necesario diseñar estos componentes desde cero dentro de Fusion 360, incluyendo su esquemático, footprint y modelo 3D. Varios paquetes de software de AutoDesk, incluido Fusion 360, están orientados a la comunidad científica y de investigación, por ende ofrecen licencias sin costo para estudiantes o miembros de universidades. Estas herramientas son excelentes opciones avanzadas y completas para el diseño de electrónica, PCB, radiofrecuencia, mecánica y muchas otras disciplinas de ingeniería.
- Para simplificar el ensamblaje del diseño, se han utilizado componentes ampliamente disponibles en el mercado. En el caso de los capacitores del circuito de alimentación, se optó por versiones modulares debido a su mayor capacidad de disipación de potencia en comparación con el resto del circuito. Además, algunos valores de capacitancia, como 10 µF y 100 µF, pueden ser difíciles de encontrar en formato SMD, lo que hizo necesario recurrir a estos componentes modulares.
- Los planos de tierra desempeñan un papel fundamental en la disipación térmica y la reducción de interferencias, por lo que ambas caras del PCB han sido cubiertas casi en su totalidad con este plano. Aunque los planos de cobre —zonas de cobre aisladas de cualquier señal y distintas al plano de tierra— también pueden contribuir a la disipación térmica, en este caso no se han implementado, ya que podrían generar interferencias en las señales I2C, SPI y UART. Además, dado que los planos de tierra ocupan la mayor parte de los espacios vacíos del PCB, la incorporación de planos de cobre no resulta necesaria.
- Este diseño incorpora una entrada USB-C, lo que permite tanto la alimentación del circuito completo como la programación del ESP32. Se ha seleccionado esta versión de USB para garantizar un proyecto moderno con conexiones estandarizadas y ampliamente utilizadas.
- A diferencia de su versión modular, desarrollada en [Modular-PCB-Design-for-Seismic-Monitoring](https://github.com/Christian-Loja/Modular-PCB-Design-for-Seismic-Monitoring), este diseño es notablemente más compacto y profesional. En lugar de incorporar módulos completos, se han seleccionado únicamente los componentes esenciales para el funcionamiento del sistema. Un claro ejemplo de esta optimización es el reemplazo del módulo `ESP32-DEVKIT` por el `ESP32-WROOM32E`, lo que mejora la eficiencia y reduce el espacio ocupado en la PCB.

### ⚠️ Precauciones  
- **Montaje**: Es fundamental verificar la polaridad de los componentes sensibles, como la entrada de 12 voltios y los capacitores electrolíticos. Para garantizar un ensamblaje seguro, se recomienda revisar los modelos 3D y los footprints antes y durante la instalación.
Además, durante el proceso de soldadura, es esencial aplicar el calor de manera controlada para evitar daños en la PCB o en los componentes. Por ello, se aconseja utilizar un cautín con temperatura regulable y una pistola de calor ajustable para un manejo preciso del calor.  
- **Adquisición de componentes**: Es crucial verificar que los componentes a adquirir cuenten con un código SMD, una versión modular o un modelo compatible con cada elemento listado en el repositorio. De lo contrario, las diferencias en dimensiones podrían impedir su correcta soldadura en la PCB.  

### 🔮 Recomendaciones  
- Implementar una etapa de protección contra sobretensiones y picos de corriente para prevenir daños en el hardware y evitar pérdidas de información.
- Considerar encapsulado/blindaje para ambientes hostiles.
- Incorporar un circuito de alimentación de respaldo para todo el sistema, ya que actualmente solo el `RTC-DS3231` cuenta con una batería que mantiene activo el reloj durante períodos de desconexión eléctrica.

---

## 📜 Licencia  
Este proyecto está bajo licencia **MIT**. Para más detalles, consulta el archivo [LICENSE](/LICENSE).  
