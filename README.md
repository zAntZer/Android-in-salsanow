
* [🇺🇸 - English](https://github.com/zAntZer/Android-in-salsanow/edit/main/en.md))
# 🚀 GFN SALSA NOW: Tutorial para Instalar Android en QEMU

Bienvenido. Este repositorio contiene las instrucciones y scripts necesarios para instalar y emular Android (Bliss OS) utilizando QEMU. 

> **Nota de la comunidad:** ¡Mientras más prueben este método, más pueden ayudar a mejorar la configuración y el rendimiento!

---

## 🛠️ Requisitos Previos

1. **Descargar QEMU:**
   Debes descargar y colocar QEMU en la siguiente ruta exacta para que los scripts funcionen por defecto:
   `I:\ANTONY\Android\QEMU`
   *Si decides extraerlo en tu propia ruta, tendrás que abrir y editar los archivos `.BAT` para modificar las rutas correspondientes.*

2. **Descargar la ISO de Bliss OS:**
   * [Descargar ISO de Android](https://gofile.io/d/Mcv32D)
   * Asegúrate de guardar el archivo en la misma carpeta de trabajo.

---

## ⚙️ Instrucciones de Instalación y Uso

### 1. Crear el Disco Virtual
Primero, necesitas crear el disco duro virtual donde residirá el sistema Android. 
Ejecuta el archivo [`CREATE.BAT`](https://github.com/zAntZer/Android-in-salsanow/blob/main/CREATE.BAT), o si prefieres la consola, usa este comando:

```cmd
qemu-img create -f qcow2 disco_bliss.qcow2 32G

```

### 2. Ejecutar la Máquina Virtual

Para iniciar el entorno, ejecuta el archivo [`RUN.BAT`](https://github.com/zAntZer/Android-in-salsanow/blob/main/RUN.BAT), el cual contiene los parámetros optimizados para arrancar QEMU:

```cmd
qemu-system-x86_64 -m 8192 -smp 1 -cpu max -drive file=disco_bliss.qcow2,format=qcow2 -cdrom bliss.iso -boot d -vga std -display sdl -net nic -net user -no-reboot

```

### 3. Configurar el Arranque (Boot)

Cuando cargue la pantalla inicial con la lista de inicios de Bliss OS, sigue estos pasos:

1. Pulsa la tecla **`TAB`**.
2. Escribe la siguiente línea justo **después** de la palabra `linux`:
```text
nomodeset HWACCEL=0 NO3D=1 DEBUG=2

```


3. Presiona **`ENTER`**.

### 4. Inicialización

Luego de esperar un momento, la pantalla te mostrará una consola de comandos (Shell) como esta:

Una vez aquí:

1. Escribe `exit` y presiona **`ENTER`**.
2. Vuelve a escribir `exit` y presiona **`ENTER`** por segunda vez.

Luego de esto, el sistema comenzará a cargar y verás el logo de Bliss OS en pantalla:

---

## 💡 Solución de Problemas (FAQ)

**No encuentro el símbolo `=` en mi teclado dentro de QEMU**
Si tienes problemas con la distribución del teclado al escribir los parámetros de arranque, haz lo siguiente:

1. Pulsa `Control` + `Alt` + `2` para abrir la consola de QEMU.
2. Escribe el comando: `sendkey equal`
3. Vuelve a la pantalla de la máquina virtual pulsando `Control` + `Alt` + `1`.
