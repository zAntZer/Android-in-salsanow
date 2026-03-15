# 📱 GFN SALSA NOW: Tutorial para instalar Android en QEMU

> **Change language >**  [![Español](https://img.shields.io/badge/Idioma-Español-red)](README.md) [![English](https://img.shields.io/badge/Language-English-blue)](en.md) <!-- Botón para versión en inglés si existe -->

¡Bienvenido al tutorial definitivo para correr **Android (Bliss OS)** dentro de QEMU!  
Perfecto para probar aplicaciones, jugar o simplemente experimentar con Android en tu PC.  
Sigue los pasos y en minutos tendrás tu máquina virtual funcionando.
> **Nota de la comunidad:** ¡Podria No funcionar, Por eso es bueno Aportar e Investigar para Mejorar!

> [!IMPORTANT]
> If you choose a different path, you **must** update the directory references in the `.bat` files accordingly.
---

## 📋 Requisitos previos

1. **QEMU** instalado en tu sistema.  
   - Descárgalo desde [QEMU WEB](https://www.qemu.org/download/) o usa el que ya tienes.  
   - **Ruta sugerida:** `I:\ANTONY\Android\QEMU`  
   - Si lo instalas en otra carpeta, **debes modificar las rutas en los archivos `.bat`** o ejecutar los comandos manualmente.

2. **ISO de Bliss OS** (Android optimizado para PC).  
   - Descarga la imagen desde este enlace:  
     [🔗 Download ISO ](https://gofile.io/d/Mcv32D)  
   - El archivo se llamará algo como `bliss.iso` (puedes renombrarlo).

3. **Espacio en disco:** Al menos 32 GB libres para el disco virtual.

---

## 🛠️ Crear el disco virtual

Ejecuta el archivo `CREATE.BAT` (disponible en el repositorio) o usa el comando manualmente:

```batch
qemu-img create -f qcow2 disco_bliss.qcow2 32G
```

Esto generará un archivo `disco_bliss.qcow2` que crecerá conforme instales apps.

📁 **CREATE.BAT** → [ver archivo](https://github.com/zAntZer/Android-in-salsanow/blob/main/CREATE.BAT)

---

## 🚀 Arrancar la máquina virtual

Usa el archivo `RUN.BAT` o ejecuta el siguiente comando (ajusta rutas si es necesario):

```batch
qemu-system-x86_64 -m 8192 -smp 1 -cpu max -drive file=disco_bliss.qcow2,format=qcow2 -cdrom bliss.iso -boot d -vga std -display sdl -net nic -net user -no-reboot
```

📁 **RUN.BAT** → [ver archivo](https://github.com/zAntZer/Android-in-salsanow/blob/main/RUN.BAT)

> **Nota:** Asigna al menos 8 GB de RAM (`-m 8192`) para un rendimiento fluido. Si tu PC tiene menos, reduce a `4096`.

---

## ⚙️ Configuración en el arranque

Cuando aparezca el menú de inicio de Bliss OS (con una lista de opciones):

1. **Pulsa la tecla `TAB`** sobre la opción seleccionada.
2. Se mostrará una línea de comandos del kernel. Al final de la línea, agrega esto:

```
nomodeset HWACCEL=0 NO3D=1 DEBUG=2
```
## ⌨️ Problemas con el teclado

Si en tu distribución de teclado no encuentras el carácter `=` (igual):

1. Presiona `Ctrl + Alt + 2` para abrir la consola de QEMU (monitor).
2. Escribe el comando:
```
sendkey equal
```
---

3. Presiona `Enter`.  
   - Verás una pantalla similar a esta:  

   ![Pantalla de carga inicial](https://raw.githubusercontent.com/zAntZer/Android-in-salsanow/main/imagen.png)

4. Cuando aparezca el mensaje, escribe `exit` y presiona `Enter` dos veces.  
   La máquina continuará arrancando y mostrará el logo de Bliss OS:

   ![Logo Bliss OS](https://raw.githubusercontent.com/zAntZer/Android-in-salsanow/main/imagen(1).png)

5. Espera a que termine la configuración inicial y ¡listo! Ya tienes Android funcionando.

---

## 🧪 Pruebas y mejoras

Este proyecto es experimental. Mientras más pruebas realices, más podremos mejorar la compatibilidad.  
Si encuentras errores o tienes sugerencias, abre un **issue** o contribuye directamente.

---

## 📌 Notas adicionales

- Los archivos `.bat` incluidos asumen que QEMU está en `I:\ANTONY\Android\QEMU`. Si no es tu caso, edítalos con un bloc de notas.
- Puedes cambiar el tamaño del disco editando el comando `qemu-img create`.
- Para un mejor rendimiento, prueba distintos valores en los parámetros del kernel (quita `DEBUG=2` si ya no lo necesitas).

---

¡Disfruta de Android en QEMU! 🎉  
Si te sirvió, no olvides dejar una ⭐ en el repositorio.

---
