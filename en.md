
# 🚀 GFN SALSA NOW: Android QEMU Installation Tutorial

Welcome! This repository contains the instructions and scripts needed to install and emulate Android (Bliss OS) using QEMU. 

> **Community Note:** The more you test this method, the more you can help improve the configuration and performance!

---

## 🛠️ Prerequisites

1. **Download QEMU:**
   You must download and extract QEMU to the following exact path for the default scripts to work:
   `I:\ANTONY\Android\QEMU`
   *If you choose to extract it to a different path, you will need to open and edit the `.BAT` files to modify the corresponding paths.*

2. **Download the Bliss OS ISO:**
   * [Download Android ISO](https://gofile.io/d/Mcv32D)
   * Make sure to save the file in the same working directory.

---

## ⚙️ Installation & Usage Instructions

### 1. Create the Virtual Disk
First, you need to create the virtual hard drive where the Android system will be installed. 
Run the [`CREATE.BAT`](https://github.com/zAntZer/Android-in-salsanow/blob/main/CREATE.BAT) file, or if you prefer the command line, use this command:

```cmd
qemu-img create -f qcow2 disco_bliss.qcow2 32G

```

### 2. Run the Virtual Machine

To start the environment, run the [`RUN.BAT`](https://github.com/zAntZer/Android-in-salsanow/blob/main/RUN.BAT) file, which contains the optimized parameters to boot QEMU:

```cmd
qemu-system-x86_64 -m 8192 -smp 1 -cpu max -drive file=disco_bliss.qcow2,format=qcow2 -cdrom bliss.iso -boot d -vga std -display sdl -net nic -net user -no-reboot

```

### 3. Configure Boot Parameters

When the initial screen with the Bliss OS boot list loads, follow these steps:

1. Press the **`TAB`** key.
2. Type the following line right **after** the word `linux`:
```text
nomodeset HWACCEL=0 NO3D=1 DEBUG=2

```


3. Press **`ENTER`**.

### 4. Initialization

After waiting a moment, the screen will show a command console (Shell) like this:

Once here:

1. Type `exit` and press **`ENTER`**.
2. Type `exit` again and press **`ENTER`** a second time.

After this, the system will start loading, and you will see the Bliss OS logo on the screen:

---

## 💡 Troubleshooting

**I can't find the `=` symbol on my keyboard inside QEMU**
If you have keyboard layout issues when typing the boot parameters, do the following:

1. Press `Ctrl` + `Alt` + `2` to open the QEMU console.
2. Type the command: `sendkey equal`
3. Return to the virtual machine screen by pressing `Ctrl` + `Alt` + `1`.

