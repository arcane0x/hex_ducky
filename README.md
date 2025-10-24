# HexDucky — The Enchanted Injector

> **A fantasy-themed USB "Rubber Ducky" built on a Digispark ATTiny85 — cast keyboard "spells" when plugged in.**

---

## ✨ Project Overview

**HexDucky** is a small, enchanted USB injector (Digispark ATTiny85) that emulates a USB keyboard and automatically types configured payloads when plugged into a host computer. Payloads are written as Arduino sketches using the `DigiKeyboard` library and named like magical spells (e.g., `ShadowSpell.ino`, `RuneOfInsight.ino`).

This repository contains setup instructions, example payloads, and ideas to give your Digispark a fantasy-themed personality.

---

## ⚙️ Core Idea

* Use a Digispark ATTiny85 to emulate a USB HID keyboard.
* Write payloads in the Arduino IDE with the DigiKeyboard library to send keystrokes.
* Give each payload a magical/fantasy name and optionally build a physical, themed casing.

---

## 🪄 Key Components

| Component                   | Description                                                                                   |
| --------------------------- | --------------------------------------------------------------------------------------------- |
| **Digispark ATTiny85**      | Tiny microcontroller that can emulate a USB HID keyboard.                                     |
| **Arduino IDE**             | Used to write and upload sketches.                                                            |
| **DigiKeyboard Library**    | Lets the ATTiny85 send keystrokes via USB (keyboard emulation).                               |
| **Fantasy Script Payloads** | Custom "spells" (Arduino `.ino` sketches) that perform actions when the device is plugged in. |

---

## 🛠️ Setup Steps

1. **Install Arduino IDE**

   If you don't have it already, download from the official site: `https://www.arduino.cc/en/software`.

2. **Add Digispark Board Support**

   * Open **File → Preferences** in Arduino IDE.
   * In **Additional Boards Manager URLs**, add:

   ```
   http://digistump.com/package_digistump_index.json
   ```

   * Then go to **Tools → Board → Boards Manager**.
   * Search for **Digistump AVR Boards** and install it.

3. **Include the DigiKeyboard Library**

   In your `.ino` sketch include:

   ```cpp
   #include "DigiKeyboard.h"
   ```

4. **Select Board & Upload**

   * In Arduino IDE select **Tools → Board → Digispark (Default - 16.5mhz)** (or the Digispark option available after installing the board package).
   * Connect the Digispark when prompted by the IDE and upload the sketch.

---

## 🔮 Example Payloads (Spells)

### Mystic Command Spell — (opens Notepad and types a fantasy message)

```cpp
#include "DigiKeyboard.h"

void setup() {
  DigiKeyboard.delay(1000);
  DigiKeyboard.sendKeyStroke(KEY_R, MOD_GUI_LEFT); // Windows + R
  DigiKeyboard.delay(500);
  DigiKeyboard.println("notepad");
  DigiKeyboard.delay(800);
  DigiKeyboard.println("✨ By the will of the Arcane Code, this system is bound! ✨");
}

void loop() {
  // Empty — spell cast only once
}
```

**Notes:**

* `DigiKeyboard.delay(ms)` waits before continuing so the system can open dialogs.
* `DigiKeyboard.sendKeyStroke(KEY_R, MOD_GUI_LEFT)` sends `Win + R` on Windows. On other platforms you may need different key combos.

---

### System Info Summoner — (open Run, launch cmd and run a system info command)

```cpp
#include "DigiKeyboard.h"

void setup() {
  DigiKeyboard.delay(1000);
  DigiKeyboard.sendKeyStroke(KEY_R, MOD_GUI_LEFT);
  DigiKeyboard.delay(500);
  DigiKeyboard.println("cmd /k echo 🔮 System Divination 🔮 && systeminfo | findstr /B /C:\"OS\" /C:\"System Type\"");
}

void loop() {}
```

**Notes:** This uses `cmd /k` to run the command and keep the terminal open. Adjust for locale differences and platform commands.

---

## ⚔️ Additional Spell Ideas

| Spell Name       | Effect                                                                        |
| ---------------- | ----------------------------------------------------------------------------- |
| **ShadowSummon** | Opens Command Prompt and runs a harmless system info command.                 |
| **GhostWhisper** | Types random “whispering” messages across the screen.                         |
| **PhoenixRise**  | Launches the default browser and opens your project's website (e.g., WizVid). |
| **ArcaneLock**   | Locks the computer with `Win + L`.                                            |
| **Divination**   | Displays system date/time using `cmd /c date /t && time /t`.                  |

---

## 🧩 Tips for Making Payloads More Reliable

* Use sensible `delay()` values to allow slower machines or locked screens time to respond.
* Test payloads only on your own systems or with explicit permission.
* Consider creating short payloads for testing (e.g., open Notepad, type a short phrase) before moving on to heavier routines.
* Escape quotes and special characters properly within `DigiKeyboard.println()`.

---

## 🧚‍♀️ Fantasy Touches (Physical + Cosmetic)

* **Engrave or paint runes** on the USB casing.
* **Add a small LED** (with a suitable resistor) to simulate "charging" while idle.
* **3D print** a wand-like or crystal-shell enclosure for the Digispark.
* Use **magical names** for payload files: `ShadowSpell.ino`, `RuneOfInsight.ino`, `PhoenixRise.ino`, etc.

---

## ⚠️ Ethical Reminder

**Only use HexDucky on your own machines, for demos, or with explicit permission.**

Unauthorized plugging of HID injectors into other people's devices can violate privacy, cause harm, and is illegal in many jurisdictions. Always follow local laws and ethical guidelines.

---

## 🧾 Suggested Repository Structure

```
HexDucky/
├─ README.md
├─ payloads/
│  ├─ MysticCommandSpell.ino
│  ├─ SystemInfoSummoner.ino
│  ├─ ShadowSummon.ino
│  └─ ArcaneLock.ino
├─ hardware/
│  ├─ enclosure.stl
│  └─ led-wiring-diagram.png
└─ LICENSE
```

---

## 🗂️ License

Include a license of your choice (MIT is common for hobby projects). Example: `LICENSE` file with MIT terms.

---

## 🪄 Final Notes

Give the project a consistent fantasy theme across code comments, file names, and the physical build. Have fun, craft responsibly, and let HexDucky be a playful learning tool for embedded HID development.

---

*Created with a little magic — keep it ethical.*
