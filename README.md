  ___  ______ _____ _____ _____ _____ _____ 
 / _ \ | ___ \_   _/  ___/  __ \_   _|_   _|
/ /_\ \| |_/ / | | \ `--.| /  \/ | |   | |  
|  _  ||    /  | |  `--. \ |     | |   | |  
| | | || |\ \  | | /\__/ / \__/\_| |_ _| |_ 
\_| |_/\_| \_| \_/ \____/ \____/\___/ \___/ 
                                            
                                            
# 📷 ASCII CAM

A real-time webcam-to-ASCII art converter that runs entirely in the browser — no server, no dependencies, no install.



## ✨ Features

- **Live camera feed** converted to ASCII art in real-time (~20 fps)
- **8 character sets** — Detailed, Simple, Blocks, Binary, Matrix, Braille, Dots, Emoji
- **8 color modes** — Real colors, Green, Amber, Cyan, Red, Purple, White, and Custom
- **Custom color picker** — choose your own dark and bright colors with gradient interpolation
- **Adjustable column density** — from 30 to 180 columns
- **Background brightness** slider
- **Mirror mode** — flip horizontally (on by default)
- **Invert mode** — swap bright/dark characters
- **Save frame** — download the current ASCII frame as a PNG
- Zero dependencies — pure HTML, CSS, and vanilla JavaScript

---

## 🚀 Quick Start

### Option 1 — Python (recommended, no install needed)

```bash
# Clone the repo
git clone https://github.com/ayuuXploits/ascii-cam.git
cd ascii-cam

# Start a local server
python -m http.server 8080
```

Then open **http://localhost:8080/ascii_cam.html** in your browser.

### Option 2 — Node.js

```bash
npx serve .
```

### Option 3 — VS Code

Install the **Live Server** extension → right-click `ascii_cam.html` → **Open with Live Server**

> ⚠️ **Why a local server?** Browsers block `getImageData()` on `file://` URLs for security reasons. Opening via `localhost` bypasses this restriction.

---

## 🎮 Controls

| Control | Description |
|---|---|
| **INIT CAMERA** | Request camera access and start the feed |
| **PAUSE / RESUME** | Freeze or unfreeze the current frame |
| **Char Set** | Switch between 8 ASCII character sets |
| **Color Mode** | Choose from 8 color palettes, including custom |
| **Custom colors** | Pick dark and bright endpoint colors for gradient mapping |
| **Columns slider** | Adjust character density (more cols = more detail) |
| **Background slider** | Control background brightness |
| **MIRROR toggle** | Flip the feed horizontally |
| **INVERT toggle** | Swap bright and dark characters |
| **SAVE FRAME** | Download the current frame as a PNG |

---

## 🗂️ Project Structure

```
ascii-cam/
└── ascii_cam.html   # Entire app — self-contained single file
```

---

## 🧠 How It Works

1. Camera feed is captured via `getUserMedia()` into a hidden `<video>` element
2. Each frame, the video is drawn into a small offscreen `<canvas>` at the target column/row resolution
3. `getImageData()` reads each pixel's RGB values
4. Each pixel's luminance maps to a character in the selected set (darker = denser character)
5. Characters are drawn onto the visible canvas using `ctx.fillText()` with the selected color mode applied
6. The loop runs at ~20 fps via `requestAnimationFrame`

---

## 🌈 Color Modes

| Mode | Description |
|---|---|
| **Real** | Each character is colored with the actual pixel color from the camera |
| **Green** | Classic terminal green monochrome |
| **Amber** | Retro amber CRT monitor style |
| **Cyan** | Cool cyan glow |
| **Red** | Dramatic red tones |
| **Purple** | Deep purple wash |
| **White** | Pure grayscale |
| **Custom** | Pick any two colors — the app interpolates between them based on brightness |

---

## 🖥️ Browser Compatibility

| Browser | Status |
|---|---|
| Chrome 80+ | ✅ Fully supported |
| Firefox 75+ | ✅ Fully supported |
| Edge 80+ | ✅ Fully supported |
| Safari 14+ | ✅ Fully supported |
| Mobile Chrome | ✅ Works (uses front camera) |

---

## 📋 Requirements

- A device with a webcam
- A modern browser (Chrome, Firefox, Edge, Safari)
- A local web server (see Quick Start above) — **required** for camera pixel access

---

## 📄 License

MIT — do whatever you want with it.

---

## 🤝 Contributing

Pull requests are welcome! Some ideas for contributions:

- Additional character sets
- Recording / GIF export
- Font size selector
- More color effects (e.g. hue rotation, sepia)
- Mobile UI improvements

---

*Built with HTML, CSS, and vanilla JavaScript. No frameworks. No bundlers. No nonsense.*
