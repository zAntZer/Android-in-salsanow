# 📱 GFN SALSA NOW: Tutorial to install Android on QEMU

> **Change language >**  [![Español](https://img.shields.io/badge/Idioma-Español-red)](README.md) [![English](https://img.shields.io/badge/Language-English-blue)](EN.md) <!-- Button for English version if exists -->

Welcome to the ultimate tutorial to run **Android (Bliss OS)** inside QEMU!  
Perfect for testing apps, gaming, or just experimenting with Android on your PC.  
Follow the steps and in minutes you'll have your virtual machine up and running.
> **Community note:** It might not work, so it's good to contribute and research to improve!

> [!IMPORTANT]
> If you choose a different path, you **must** update the directory references in the `.bat` files accordingly.

---

## 📋 Prerequisites

1. **QEMU** installed on your system.  
   - Download it from [QEMU WEB](https://www.qemu.org/download/) or use the one you already have.  
   - **Suggested path:** `I:\ANTONY\Android\QEMU`  
   - If you install it in another folder, you **must modify the paths in the `.bat` files** or run the commands manually.

2. **Bliss OS ISO** (Android optimized for PC).  
   - Download the image from this link:  
     [🔗 Download ISO](https://gofile.io/d/Mcv32D)  
   - The file will be named something like `bliss.iso` (you can rename it).

3. **Disk space:** At least 32 GB free for the virtual disk.

---

## 🛠️ Create the virtual disk

Run the `CREATE.BAT` file (available in the repository) or use the command manually:

```batch
qemu-img create -f qcow2 disco_bliss.qcow2 32G
```

This will generate a `disco_bliss.qcow2` file that grows as you install apps.

📁 **CREATE.BAT** → [view file](https://github.com/zAntZer/Android-in-salsanow/blob/main/CREATE.BAT)

---

## 🚀 Start the virtual machine

Use the `RUN.BAT` file or run the following command (adjust paths if necessary):

```batch
qemu-system-x86_64 -m 8192 -smp 1 -cpu max -drive file=disco_bliss.qcow2,format=qcow2 -cdrom bliss.iso -boot d -vga std -display sdl -net nic -net user -no-reboot
```

📁 **RUN.BAT** → [view file](https://github.com/zAntZer/Android-in-salsanow/blob/main/RUN.BAT)

> **Note:** Assign at least 8 GB of RAM (`-m 8192`) for smooth performance. If your PC has less, reduce it to `4096`.

---

## ⚙️ Boot configuration

When the Bliss OS boot menu appears (with a list of options):

1. **Press the `TAB` key** on the selected option.
2. A kernel command line will be shown. At the end of the line, add this:

```
nomodeset HWACCEL=0 NO3D=1 DEBUG=2
```

## ⌨️ Keyboard issues

If your keyboard layout doesn't have the `=` (equals) character:

1. Press `Ctrl + Alt + 2` to open the QEMU console (monitor).
2. Type the command:
```
sendkey equal
```
3. Press `Enter`.  
   - You'll see a screen similar to this:  

   ![Initial boot screen](https://raw.githubusercontent.com/zAntZer/Android-in-salsanow/main/imagen.png)

4. When the message appears, type `exit` and press `Enter` twice.  
   The machine will continue booting and show the Bliss OS logo:

   ![Bliss OS logo](https://raw.githubusercontent.com/zAntZer/Android-in-salsanow/main/imagen(1).png)

5. Wait for the initial setup to finish and voilà! Android is now running.

---

## 🧪 Testing and improvements

This project is experimental. The more you test, the more we can improve compatibility.  
If you find bugs or have suggestions, open an **issue** or contribute directly.

---

## 📌 Additional notes

- The included `.bat` files assume QEMU is located at `I:\ANTONY\Android\QEMU`. If that's not your case, edit them with a text editor.
- You can change the disk size by editing the `qemu-img create` command.
- For better performance, try different values in the kernel parameters (remove `DEBUG=2` if you no longer need it).

---

Enjoy Android on QEMU! 🎉  
If it helped you, don't forget to leave a ⭐ on the repository.

---
