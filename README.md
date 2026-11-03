# Mouse Reactive Floating Image

### ₊⊹ About

This is a **mouse reactive floating image** gallery. It places an oversized grid of visual assets behind the viewport, hidden by the overflow. Tis function is to provide an immersive, explorative navigation experience where the user's cursor physically steers the scene across a scattered landscape of content.

https://github.com/user-attachments/assets/daddc9b5-633c-4a97-96b0-2040c1ec7060

---

### ★ Features

- Mouse tracking
- Smooth panning
- Hover reveal
- Dynamic layout

---

### .ᐟ.ᐟ How It Works

- 1. **Gallery larger than the screen:** `#gallery` is a square measuring `140vmax` by `140vmax`, positioned with `position: absolute`. The `vmax` unit uses the longest side of the window, so the gallery is always larger than the screen, regardless of the aspect ratio.
- 2. **Only a portion is visible:** The `body` has `overflow: hidden`, so the screen shows only a portion of the gallery, and no scrollbars appear.
- 3. **Colored blocks:** Each `.tile` is positioned with `position: absolute`, with its size and position specified as percentages within the gallery (`nth-child` defines the background color, size, and position of each one). The images start with `opacity: 0`, so only the colors are visible at first.
- 4. **Mouse position:** On the `mousemove` event, JavaScript divides the mouse position by the window size and obtains a value between `0` and `1` for each axis (`xDecimal` and `yDecimal`).
- 5. **How far the gallery can move:** `maxX` and `maxY` are the difference between the gallery’s size and the window’s size—that is, the part of the gallery that is off-screen.
- 6. **Reverse movement:** `panX` and `panY` multiply this extra space by the mouse value and by `-1`. With the mouse in the left corner, the gallery starts at the beginning, and with it in the right corner, it scrolls to the end. Since the value is negative, the gallery moves in the opposite direction of the mouse, as if you were exploring a map larger than the screen.
- 7. **Smooth movement:** `gallery.animate()` applies the `translate` property using the Web Animations API, over `4000ms` with `ease`. The movement follows the mouse with a smooth delay, and `fill: “forwards”` keeps the gallery in its final position when the animation ends.
- 8. **Hover effect:** When you hover over a block, it scales up with `scale(1.1)`, the image appears with `opacity: 1`, and gains a slight `scale(1.01)`. Both transitions last `800ms`.
- 9. **Rounded corners:** The `.tile` class has `border-radius: 1vmax`, and the image uses `border-radius: inherit` to match the block’s shape.

---

### ⚙️ Tech Stack

- **HTML**
- **CSS**
- **JavaScript**

---

### 🖿 Project structure

```
project-name/
├── index.html
├── Styles.css
└── README.md
```

---

### 📖 What i learned

- **HTML:** Organize a gallery with a main `div` and several blocks (`.tile`), each containing an image
- **CSS:** Use the `vmax` unit to create a gallery larger than the screen, regardless of the window's aspect ratio
- **CSS:** `overflow: hidden` on the `body` to show only a portion of the gallery, without scrollbars
- **CSS:** `position: absolute` with sizes and positions in percentages to spread out the blocks
- **CSS:** `:nth-child` to give each block a different color, size, and position
- **CSS:** reveal the image on `:hover` using `opacity` and `scale`, with transitions
- **CSS:** `border-radius: inherit` so the image follows the block’s rounded corner
- **JavaScript:** the `mousemove` event and the `clientX` and `clientY` properties to read the mouse position
- **JavaScript:** convert the mouse position to a value between `0` and `1` by dividing by the window size
- **JavaScript:** Calculate how far the gallery can move by subtracting the window size from the gallery size
- **JavaScript:** `element.animate()` from the Web Animations API, with `fill: “forwards”` to move the gallery smoothly
