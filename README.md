# XConvert_Ultimate_OGXBOX (Dual Engine) 🎮

**La navaja suiza definitiva para la optimización, conversión masiva y preservación de juegos de la Xbox Original.**

**Desarrollado por:** [Deilan-glitch](https://github.com/Deilan-glitch)

---

## 📝 Descripción

**XConvert_Ultimate_OGXBOX** es una avanzada aplicación de escritorio con interfaz gráfica (GUI) diseñada para automatizar por completo el flujo de trabajo con copias de seguridad de la Xbox Clásica. Fusiona de forma simbiótica el poder de dos de los motores más respetados de la *scene*: **extract-xiso** y **XGDTool**, empaquetándolos dentro de una "tubería" (pipeline) inteligente y automatizada.

El programa está pensado tanto para usuarios de hardware real (discos FATX) como para entusiastas de la emulación moderna (**Xemu**), permitiendo limpiar imágenes, reducir tamaños y cambiar formatos de manera masiva con un control absoluto contra fallos o redundancias humanas.

---

## ✨ Características de Nivel Profesional (Killer Features)

* **🔄 Arquitectura Híbrida (Dual Engine Pipeline):** Olvídate de decidir qué herramienta usar. El programa normaliza de forma inteligente cualquier formato de entrada (ISO estándar, XISO, carpeta HDD Ready o CCI), haciendo llamadas dinámicas en segundo plano y enrutando los procesos al motor óptimo en cada fase.
* **🔍 Escáner Hexadecimal en Tiempo Real:** Al cargar una imagen `.iso`, la herramienta viaja directamente al *Sector 32* (Offset `0x10000`) para buscar la cabecera original `MICROSOFT*XBOX*MEDIA`. Esto permite diferenciar de manera infalible si una ISO es un volcado puro e hinchado de Redump (`[STD_ISO]`) o una imagen optimizada para emulador (`[XISO]`).
* **🧼 Auto-Scrubbing de Alta Eficiencia:** Convierte copias "obesas" de formato estándar (`STD_ISO`) de Ej. 7.28 GB a impecables `XISO` optimizados de Ej. ~2 GB. El programa extrae quirúrgicamente solo los archivos reales del juego, eliminando particiones de video redundantes y sectores basura (*padding*) para un ahorro radical de espacio en PC.
* **🔥 Forzar Rewrite (Control Total):** ¿Tienes un XISO mal hecho o lleno de basura? Activa esta función para ignorar el bloqueo de redundancia y enviar el archivo a la tubería de limpieza extrema, reconstruyendo la imagen desde cero y etiquetándola automáticamente como `[Rewrite]`.
* **🛑 Filtro Anti-Torpeza y Lista Roja (Visual UX):** Al cambiar el formato de salida deseado, la lista analiza tu cola de procesamiento en tiempo real. Si detecta redundancias (como intentar convertir un CCI a un CCI), pintará automáticamente los juegos en **Rojo Pastel** y los omitirá de forma segura al iniciar el proceso para no desperdiciar ciclos de CPU.
* **🏷️ Smart Tags & Sanitización FATX Segura:** El programa extrae el título de cabecera real desde el binario interno `default.xbe`. Si la salida va a la consola (HDD Ready o CCI), calcula las dimensiones dinámicamente y recorta el título para que junto a sus etiquetas de origen (`[Src_HDD]`, `[Src_CCI]`) jamás violen el estricto límite de **42 caracteres de FATX**.
* **🌗 Motor de Temas Dinámico (Hot-Swappable UI):** Alterna instantáneamente entre un estilizado **Modo Oscuro** (Gris espacial `#1e1e1e` y consola de depuración verde neón) y un limpio **Modo Claro**. Incluye correcciones nativas (`style.map`) para evitar bugs visuales de lectura.
* **📊 Barra de Progreso General:** Un indicador de progreso visual que te mantiene al tanto de las subfases del pipeline para cada título individual.

---

## 🗂 Formatos de Salida Soportados

1. **Extraer a HDD Ready (Classic Edition):** Ideal para softmods tradicionales, exploits antiguos o almacenamiento estándar de archivos sueltos en el disco duro. Conserva la estructura LBA.
2. **Comprimir a CCI + Attacher (CerBIOS Edition):** Comprime tu colección a nivel de bloques para ahorrar el máximo espacio posible, inyectando el *attacher* universal (`default.xbe`) en la raíz del directorio de salida.
3. **Crear Imagen XISO (Emulator/PC Edition):** Genera imágenes limpias, ligeras y con mapa de sectores LBA perfectamente armado, ideales para arrancar al instante desde **Xemu**.

---

## 📥 Instalación y Uso (Plug & Play)

**XConvert_Ultimate se distribuye como un paquete "Todo en Uno".** No necesitas buscar ni descargar dependencias externas. Los motores de conversión ya vienen incluidos en la descarga oficial para garantizar un 100% de compatibilidad.

1. **Descarga** el archivo `.zip` desde la pestaña de *Releases* de este repositorio.
2. **Extrae** la carpeta en tu PC. La estructura lista para usar se verá así:
```text
📁 XConvert_Ultimate_OGXBOX/
│
├── 📄 XConvert_Ultimate.exe          (La Interfaz Gráfica)
├── 🛠️ extract-xiso.exe               (Motor incluido)
└── 🛠️ XGDTool-v1.0.0-win-x64-CLI.exe (Motor incluido)

```


3. **Ejecuta `XConvert_Ultimate.exe**`. El programa enlazará los motores automáticamente.
4. **Carga tus juegos:** Usa el botón de archivos para ISOs, o el de carpetas seleccionando tu directorio raíz para que el escáner inteligente inspeccione y cargue todos tus juegos de golpe.
5. **Configura y Ejecuta:** Elige el formato de salida, define la carpeta destino y presiona iniciar. El software creará entornos aislados temporales y destruirá los residuos automáticamente al finalizar.

---

## 🛠️ Compilación para Desarrolladores (PyInstaller)

Si realizas modificaciones en el código fuente de Python y deseas compilar el programa a un binario `.exe` independiente en Windows:

1. Instala el entorno de compilación: `pip install pyinstaller`
2. Asegúrate de contar con un archivo de ícono (`icono.ico`) en el mismo directorio.
3. Ejecuta la orden de compilación limpia:
```cmd
pyinstaller --noconsole --onefile --icon="icono.ico" "XConvert_Ultimate.py"

```


4. El ejecutable se generará en el directorio `./dist/`. Simplemente muévelo a una carpeta junto con los motores `extract-xiso.exe` y `XGDTool.exe` para mantener el paquete funcional.

---

## 📜 Créditos y Agradecimientos

**XConvert_Ultimate_OGXBOX** actúa como una interfaz puente de automatización. Todo el mérito técnico de compresión y desarmado nativo pertenece a los autores de las utilidades de código abierto:

* **wiredopposite:** Por el desarrollo y optimización del motor moderno XGDTool.
* **XboxDev Team:** Por mantener al día el estándar de la industria `extract-xiso`.
* A toda la comunidad de **OGXbox** por continuar preservando la historia del hardware y el desarrollo casero.
