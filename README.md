# 🧨 Bomberman DOM

Multiplayer Bomberman-style game built without Canvas or WebGL, powered by a custom framework and WebSockets.

## 👥 Authors

* Mohamed El-Fihry
* Oussama Benali
* Omar Ait Benhammou
* Ibrahim El Harraq

---

## 📌 Overview

Bomberman DOM is a real-time multiplayer browser game inspired by the classic Bomberman.

The game supports **2–4 players** connected through **WebSockets**, battling until only one survives.
It is built entirely using our custom framework from the `mini-framework` project.

No Canvas. No WebGL. No external frontend frameworks.

Performance was a core requirement:

* 60 FPS minimum
* No frame drops
* Proper `requestAnimationFrame` usage
* Performance measurement and optimization

---

## 🏗 Project Structure

```
bomberman-dom/
│
├── backend/        → WebSocket server (Node.js)
├── frontend/       → Game client (DOM-based rendering)
└── mini-framework/ → Custom framework used by the game
```

---

## 🎮 Game Features

### Players

* 2–4 players
* 3 lives each
* Last player alive wins

### Map

* Fixed visible map
* Two block types:

  * 🔲 Indestructible walls (static)
  * 📦 Destructible blocks (randomly generated)
* Safe spawn zones in the four corners

### Power-Ups (random drop from destroyed blocks)

* 💣 **Bombs** → Increase simultaneous bombs
* 🔥 **Flames** → Increase explosion range
* ⚡ **Speed** → Increase movement speed

---

## 💬 Multiplayer & Chat

* Real-time multiplayer using WebSockets
* Built-in chat system
* Nickname system before joining
* Waiting room with player counter
* Auto-start rules:

  * If 4 players join → 10 second countdown starts
  * If 2–3 players join and 20 seconds pass → 10 second countdown starts

---

## ⚡ Performance Strategy

* `requestAnimationFrame` used correctly
* Game loop optimized for 60 FPS
* Signals used for reactive real-time game updates
* Diffing used during login & waiting screens
* Minimal DOM updates during gameplay
* Efficient state synchronization

---

## 🧠 Technical Stack

### Frontend

* Vanilla JavaScript
* Custom framework
* DOM rendering (no Canvas)
* Signals-based reactivity

### Backend

* Node.js
* WebSockets (`ws`)

---

## 🚀 How to Run

### 1️⃣ Backend

```bash
cd backend
npm install
node app.js
```

### 2️⃣ Frontend

Open `frontend/index.html` in your browser
(or serve it using a simple local server)

Example:

```bash
cd frontend
npx serve .
```

---

## 🏁 Game Flow

1. Enter nickname
2. Join waiting room
3. Countdown starts
4. Game begins
5. Last survivor wins

---

## 🧪 Concepts Practiced

* requestAnimationFrame
* Event loop
* FPS measurement
* Multiplayer synchronization
* WebSockets
* Performance optimization
* Real-time state management

---

---

# ⚙️ Mini Framework

A lightweight JavaScript framework implementing DOM abstraction, routing, state management, event handling, signals, and diffing.

## 👥 Authors

* Mohamed El-Fihry
* Oussama Benali
* Omar Ait Benhammou
* Ibrahim El Harraq

---

## 📌 Overview

This project is a custom-built JavaScript framework created from scratch.

The goal was to understand how modern frameworks work internally by implementing:

* DOM abstraction
* Routing system
* State management
* Custom event system
* Signals (reactivity)
* Diffing (Virtual DOM strategy)

No React, Vue, Angular, or external libraries were used.

---

## 🧩 Core Features

### 1️⃣ DOM Abstraction

The DOM is represented as JavaScript objects:

```js
{
  tag: "div",
  attrs: { class: "container" },
  children: []
}
```

This allows:

* Programmatic DOM creation
* Easier manipulation
* Efficient updates via diffing

---

### 2️⃣ Diffing (Virtual DOM Concept)

* A virtual representation of the DOM is created
* Differences are calculated
* Only changed elements are updated
* Minimizes unnecessary re-renders

Used heavily in:

* Login page
* Waiting room
* Static UI parts

---

### 3️⃣ Signals (Reactive System)

Signals provide reactive state updates:

* State changes automatically update UI
* Optimized for real-time performance
* Used in the Bomberman game loop

Signals were chosen for gameplay because:

* Faster updates
* Less overhead than full diffing
* Better performance at 60 FPS

---

### 4️⃣ Routing System

* URL synchronized with application state
* Simple client-side routing
* State preserved across pages

---

### 5️⃣ State Management

* Centralized global state
* Accessible across components
* Updates propagate automatically

---

### 6️⃣ Custom Event Handling

Developers interact with events through a custom API.

Internally:

* `addEventListener` is used
* Externally:

  * Clean abstraction
  * Framework-controlled event system

---

## 📝 TodoMVC Implementation

A full TodoMVC application was built using the framework to validate:

* State handling
* Routing
* Events
* DOM updates
* Diffing behavior

All required HTML structure, IDs, and classes are present.

---

## 🏗 Framework Structure

```
mini-framework/
└── src/
    ├── core/
    │   ├── dom.js
    │   ├── events.js
    │   ├── router.js
    │   ├── signal.js
    │   └── state.js
    └── mini-framework-z01.js
```

---

## 🚀 How to Use

Include the framework script:

```html
<script src="mini-framework-z01.js"></script>
```

Create elements using the framework API:

```js
createElement("div", { class: "box" }, [])
```

Attach events:

```js
on("click", handler)
```

Manage state:

```js
setState({ count: 1 })
```

---

## 🎯 Concepts Learned

* Inversion of control
* Virtual DOM & diffing
* Signals & reactivity
* Routing
* State synchronization
* Event abstraction
* Framework architecture

---

## 🔥 Why This Matters

Instead of just using a framework, this project focuses on understanding:

* How frameworks control application flow
* How rendering optimization works
* How reactivity is implemented internally
* How multiplayer games require efficient state updates

