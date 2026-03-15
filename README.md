# GFN SALSA NOW: Tutorial para Instalar Android en QEMU

¡Bienvenido! Este repositorio contiene las instrucciones y comandos necesarios para virtualizar Android (Bliss OS) utilizando QEMU. 

> **Nota para la comunidad:** ¡Mientras más prueben, más pueden ayudar a mejorar el rendimiento y la compatibilidad! Todas las pruebas son bienvenidas.

---

## 🛠️ Requisitos Previos

1. **QEMU:** Debes tener QEMU descargado en tu sistema.
   * **Ruta por defecto:** Los scripts están configurados para funcionar en la ruta `I:\ANTONY\Android\QEMU`.
   * *Importante:* Si colocas QEMU en una ruta diferente, **tendrás que modificar las rutas dentro de los archivos `.BAT`** para que correspondan a tu directorio.
2. **Imagen ISO:** Descarga la ISO de Android desde el siguiente enlace: 
   * 📥 [Descargar ISO (gofile.io)](https://gofile.io/d/Mcv32D)
   * *(Nota: Asegúrate de que el archivo descargado se llame `bliss.iso` o coincida con el nombre en el script de ejecución).*

---

## 🚀 Instrucciones de Instalación y Ejecución

### 1. Crear el Disco Virtual
Primero, necesitamos crear el disco duro virtual (formato qcow2) de 32GB donde se alojará el sistema. 

Puedes ejecutar el script **[CREATE.BAT](https://github.com/zAntZer/Android-in-salsanow/blob/main/CREATE.BAT)** o abrir tu terminal y usar el siguiente comando:

```bash
qemu-img create -f qcow2 disco_bliss.qcow2 32G
