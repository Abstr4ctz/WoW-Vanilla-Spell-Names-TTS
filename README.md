# WoW Vanilla & TurtleWoW TTS Spell & Item Names  

https://github.com/user-attachments/assets/831ac63f-4da5-4853-ac11-baa1f00380ca

This repository contains **TTS (Text-to-Speech) spell and item names** for **WoW Vanilla** and **TurtleWoW**.  

## 📌 Purpose  
- Useful for **players** and **addon creators** who need accurate spell/item names for TTS applications.  

## 💡 Contributing  
- If you notice **missing spell names**, feel free to contribute by submitting them.

## ✨ Create your own  

## 🔧 Troubleshooting  
If you run into issues, check these resources:  
- 🔍 [Google](https://google.com/)  
- 💬 [ChatGPT](https://chatgpt.com/)  

---

Enjoy and happy modding! 🎮🔥  

---

# Edge TTS Batch Processing Guide

## 📌 Overview
This guide will walk you through installing **Edge TTS (Microsoft's TTS system)**, creating a **Python script** to generate **batch MP3 files**, and finally **editing them in Audacity** for professional quality. This is a beginner-friendly step-by-step tutorial with links and examples.

---

## 🔎 Finding Available Voices
To see a full list of available voices, run the following command:
```sh
edge-tts --list-voices
```
This will display all available voices, along with their language codes. You can change the voice in the script by modifying the `VOICE` variable.

---

## 💾 Installation

### 1️⃣ Install Python
**Edge TTS** requires **Python** to run. If you haven't installed it yet:
- **Download Python** from the official site: [https://www.python.org/downloads/](https://www.python.org/downloads/)
- Check **"Add Python to PATH"** during installation.
- Open **Command Prompt** (`Win + R`, type `cmd`, press Enter) and run:
  ```sh
  python --version
  ```
  This should display the Python version, confirming the installation.

### 2️⃣ Install Edge TTS
Once Python is installed, install Edge TTS by running:
```sh
pip install edge-tts
```
This will install Microsoft's **Edge TTS** module, which allows you to generate text-to-speech audio using their voices.

---

## 🔊 Generating TTS Files in Batch
### 1️⃣ Prepare a Text File with Words
Create a new file called **`words.txt`**, and list all the words or phrases you want to generate TTS for, one per line:
```
Fireball
Frostbolt
Arcane Explosion
Healing Touch
```  

### 2️⃣ Create a Python Script
Open a text editor (Notepad, VS Code, or PyCharm) and create a new file **`batch_tts.py`**. Copy and paste the following code:

```python
import edge_tts
import os
import asyncio

# Read words from file
with open("words.txt", "r") as file:
    words = [line.strip() for line in file]

# Output folder
output_folder = "Asilia"
os.makedirs(output_folder, exist_ok=True)

# Voice selection (change to different voices like "en-KE-AsiliaNeural")
VOICE = "en-KE-AsiliaNeural"

async def generate_tts(word):
    filename = os.path.join(output_folder, f"{word}.mp3")
    tts = edge_tts.Communicate(word, VOICE)
    await tts.save(filename)
    print(f"Saved: {filename}")

async def main():
    await asyncio.gather(*(generate_tts(word) for word in words))

asyncio.run(main())
print("TTS generation complete!")
```

### 3️⃣ Run the Script
Save the file and run it using **Command Prompt**:
```sh
python batch_tts.py
```
This will generate **MP3 files** in the `Asilia` folder.

---

## 🎵 Editing TTS Files in Audacity

### 🔹 Install Audacity
- **Download & Install Audacity** from [https://www.audacityteam.org/download/](https://www.audacityteam.org/download/)

### 🔹 Batch Processing in Audacity
1. Open **Audacity**
2. Go to **Tools → Macros**
3. Click **New** and name it **"TTS Processing"**
4. Click **Insert** and add effects in this order:
   - **Filter Curve EQ** → Reduce bass & treble slightly
   - **Normalize** → Set final loudness to `0.0 dB`
   - **Change Tempo** → Adjust speed if necessary
   - **Export as OGG** → Export to `C:\Users\You\Documents\Audacity`
5. Click **Manage Macros → Apply to Files**, select all MP3s, and process them in batch.

---

## 📝 Notes
- To see **available voices**, visit [this site](https://learn.microsoft.com/en-us/azure/ai-services/speech-service/language-support?tabs=tts).
- Change the **voice** in the script (`en-KE-AsiliaNeural`) to any supported voice.
- Adjust **EQ, compression, and normalization** in Audacity for smoother audiobook results.

---

## 📌 Conclusion
You now have a fully automated **TTS batch processing pipeline** with **Edge TTS & Audacity**! 🚀



