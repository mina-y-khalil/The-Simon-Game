# The Simon Game

<p align="center">
  <img src="https://redeem-innovations.com/wp-content/uploads/2025/09/The-simon-game.png" alt="The Simon Game preview" />
</p>

A classic memory game built with **HTML**, **CSS**, **JavaScript**, and **jQuery**.

---

## 🎮 Gameplay

Repeat the color sequence shown by the game. Each level adds one more color. One mistake ends the game and resets the level.

- **Start:** Press any key (or click, if enabled).
- **Input:** Click the colored pads in order.
- **Game Over:** Screen flashes and title updates; press any key to restart.

---

## 🧠 What This Project Demonstrates (jQuery)

- Event handling: `keydown`, `.on("click")`
- DOM manipulation: `$("#level-title").text(...)`, `$(".btn").addClass(...)`
- Simple animations: `.fadeIn().fadeOut()`, press effect via classes
- Audio playback via JS with jQuery flow control
- Basic game state management with arrays and counters

---

## 🗂️ Project Structure

```
.
├── index.html
├── styles.css
├── index.js
├── images/
│   ├── favicon.png
│   └── bg.jpg
└── sounds/
    ├── red.mp3
    ├── blue.mp3
    ├── green.mp3
    ├── yellow.mp3
    └── wrong.mp3
```

---

## 🚀 Quick Start

1. Ensure the folder structure above is in place and sound/image paths match.
2. Open `index.html` in a browser.
3. Hard refresh once if favicon doesn’t appear (Cmd/Ctrl + Shift + R).

> If hosting, serve the folder with any static server (e.g., `python -m http.server`) to avoid path issues.

---

## 🔧 Core Logic (Excerpt)

```js
var buttonColours = ["red", "blue", "green", "yellow"];
var gamePattern = [],
  userClickedPattern = [];
var started = false,
  level = 0;

$(document).on("keydown click", function () {
  if (!started) {
    $("#level-title").text("Level " + level);
    nextSequence();
    started = true;
  }
});

$(".btn").on("click", function () {
  var userChosenColour = $(this).attr("id");
  userClickedPattern.push(userChosenColour);
  playSound(userChosenColour);
  animatePress(userChosenColour);
  checkAnswer(userClickedPattern.length - 1);
});
```

---

## 🎨 Notes

- Favicon: `<link rel="icon" href="images/favicon.png" type="image/png">`
- Background image set via CSS: `images/bg.jpg`
- Button press and game-over styles handled with CSS classes.

---

## ✅ Requirements

- jQuery CDN (included in `index.html`)
- Sound files placed exactly at `sounds/<color>.mp3` and `sounds/wrong.mp3`
