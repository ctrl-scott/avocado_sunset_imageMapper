# Avocado–Sunset Pixel Mapper with Grid, Progress, and Histogram

This repository contains an educational JavaScript visualization that demonstrates **programmatic pixel mapping** on an image — specifically, a composite image of an avocado and a sunset. It provides real-time insights into how pixel-level operations are performed in digital image processing, including logging, event tracking, and statistical visualization.

The demo overlays an `(x, y)` coordinate grid over the original image without modifying it, while a pixel-mapping algorithm analyzes and transforms color regions (e.g., darkening avocado-green areas) in the base canvas. Real-time logs, a progress bar, and a histogram reflect the ongoing mapping process.

---

## 🖼️ Features

- **Dual-Canvas Architecture**:  
  - `baseCanvas` holds the actual image and pixel data.  
  - `overlayCanvas` displays an `(x, y)` grid overlay that never alters the image pixels.

- **Detailed Logging System**:  
  The in-browser console-style window records:
  - Loop and function activity  
  - Pixel coordinates and RGBA transformations  
  - Row-wise checkpoints and completion updates

- **Event Timeline Window**:  
  Provides concise, time-ordered summaries of the mapping process (start, percent progress, completion).

- **Dynamic Progress Bar**:  
  Reflects how many pixels have been processed in real-time.

- **Live RGB Histogram**:  
  Displays the average red, green, and blue values of all pixels processed so far.

- **Educational Transparency**:  
  Designed to visually show what happens inside nested loops and color-mapping functions — ideal for classroom, research, or developer education settings.

---

## 🧠 How It Works

The pixel mapping logic is built around a nested loop:

```js
for (let y = 0; y < h; y++) {
  for (let x = 0; x < w; x++) {
    const idx = (y * w + x) * 4;   // RGBA index in flat array
    let r = data[idx];
    let g = data[idx + 1];
    let b = data[idx + 2];
    let a = data[idx + 3];

    if (isAvocadoGreen(r, g, b)) {
      data[idx]     = 60;
      data[idx + 1] = 70;
      data[idx + 2] = 20;
      data[idx + 3] = a;
    }
  }
}
```
The isAvocadoGreen() function classifies avocado pixels by checking relative dominance of the green channel:
```js
function isAvocadoGreen(r, g, b) {
  return (g > 70 && g > r + 10 && g > b + 10 && r < 120 && b < 120);
}
```

This allows selective remapping (darkening avocado areas) without disturbing the vivid sunset region.

```
⚙️ Setup and Usage

Place your composite image (for example avocado_sunset.png) in the same directory.

Save the HTML file from this repository as avocado_mapper_grid.html.

Open it in any modern browser (Chrome, Firefox, Safari).

Click “Run Detailed Mapping” to execute the mapping and watch:

Log entries appear in real time.

Progress bar update dynamically.

Histogram reflect RGB changes as pixels are processed.
```
Here’s a comprehensive **GitHub `README.md`** for your avocado–sunset pixel mapping project, written in professional documentation style, including detailed technical explanation, usage instructions, and properly formatted **APA-style citations** (none of which reference you personally).

---

````markdown
# Avocado–Sunset Pixel Mapper with Grid, Progress, and Histogram

This repository contains an educational JavaScript visualization that demonstrates **programmatic pixel mapping** on an image — specifically, a composite image of an avocado and a sunset. It provides real-time insights into how pixel-level operations are performed in digital image processing, including logging, event tracking, and statistical visualization.

The demo overlays an `(x, y)` coordinate grid over the original image without modifying it, while a pixel-mapping algorithm analyzes and transforms color regions (e.g., darkening avocado-green areas) in the base canvas. Real-time logs, a progress bar, and a histogram reflect the ongoing mapping process.

---

## 🖼️ Features

- **Dual-Canvas Architecture**:  
  - `baseCanvas` holds the actual image and pixel data.  
  - `overlayCanvas` displays an `(x, y)` grid overlay that never alters the image pixels.

- **Detailed Logging System**:  
  The in-browser console-style window records:
  - Loop and function activity  
  - Pixel coordinates and RGBA transformations  
  - Row-wise checkpoints and completion updates

- **Event Timeline Window**:  
  Provides concise, time-ordered summaries of the mapping process (start, percent progress, completion).

- **Dynamic Progress Bar**:  
  Reflects how many pixels have been processed in real-time.

- **Live RGB Histogram**:  
  Displays the average red, green, and blue values of all pixels processed so far.

- **Educational Transparency**:  
  Designed to visually show what happens inside nested loops and color-mapping functions — ideal for classroom, research, or developer education settings.

---

## 🧠 How It Works

The pixel mapping logic is built around a nested loop:

```js
for (let y = 0; y < h; y++) {
  for (let x = 0; x < w; x++) {
    const idx = (y * w + x) * 4;   // RGBA index in flat array
    let r = data[idx];
    let g = data[idx + 1];
    let b = data[idx + 2];
    let a = data[idx + 3];

    if (isAvocadoGreen(r, g, b)) {
      data[idx]     = 60;
      data[idx + 1] = 70;
      data[idx + 2] = 20;
      data[idx + 3] = a;
    }
  }
}
````

The `isAvocadoGreen()` function classifies avocado pixels by checking relative dominance of the green channel:

```js
function isAvocadoGreen(r, g, b) {
  return (g > 70 && g > r + 10 && g > b + 10 && r < 120 && b < 120);
}
````

This allows selective remapping (darkening avocado areas) without disturbing the vivid sunset region.

---

## ⚙️ Setup and Usage

1. Place your **composite image** (for example `avocado_sunset.png`) in the same directory.
2. Save the HTML file from this repository as `avocado_mapper_grid.html`.
3. Open it in any modern browser (Chrome, Firefox, Safari).
4. Click **“Run Detailed Mapping”** to execute the mapping and watch:

   * Log entries appear in real time.
   * Progress bar update dynamically.
   * Histogram reflect RGB changes as pixels are processed.

---

## 🧩 File Structure

```
avocado_mapper_grid.html   # Main visualization and code
avocado_sunset.png         # Source image (avocado + sunset composite)
README.md                  # Project documentation
```

---

## 🧮 Technical Notes

* Uses **HTML5 Canvas API** (`getImageData` / `putImageData`) for pixel-level access.
* Two stacked canvases separate processing from visualization layers.
* Performance scales with image size; ideal for < 1000×1000 px for smooth logging.
* 100% client-side; no external dependencies or frameworks required.
* Progress and histogram calculations are updated every 20,000 pixels for efficiency.

---

## 📚 References (APA Style)

* Adobe. (2023). *Understanding pixels and resolution in digital images.* Adobe Help Center.
  [https://helpx.adobe.com/photoshop/using/image-size-resolution.html](https://helpx.adobe.com/photoshop/using/image-size-resolution.html)

* Mozilla Developer Network. (2024). *CanvasRenderingContext2D: getImageData() method.*
  MDN Web Docs. [https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/getImageData](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/getImageData)

* Mozilla Developer Network. (2024). *Working with ImageData objects in Canvas.*
  MDN Web Docs. [https://developer.mozilla.org/en-US/docs/Web/API/ImageData](https://developer.mozilla.org/en-US/docs/Web/API/ImageData)

* Pillow Developers. (2023). *The Python Imaging Library (Pillow) documentation.*
  [https://pillow.readthedocs.io/](https://pillow.readthedocs.io/)

* W3C. (2022). *HTML Living Standard: The canvas element.*
  [https://html.spec.whatwg.org/multipage/canvas.html](https://html.spec.whatwg.org/multipage/canvas.html)

* Sora AI & Freeform. (2025). *Composite imagery of avocado and sunset used under fair use for educational demonstration.*

---

## 🧑‍🏫 Educational Purpose and Ethics

This visualization is designed for **non-commercial educational use** in demonstrating digital image manipulation, logging, and visual feedback loops.
It emphasizes algorithmic transparency and ethical educational illustration rather than production-level optimization or obfuscation.

---

## 🪪 License

MIT License © 2025
Permission is granted to use, copy, modify, and distribute this software for educational and research purposes.

---

## 🖋️ Suggested Citation

If referencing this work in academic or technical materials, please cite it as:

> “Avocado–Sunset Pixel Mapper with Grid and Histogram” (2025). Educational visualization demonstrating programmatic pixel mapping using HTML5 Canvas and JavaScript. GitHub Repository.

```

---
