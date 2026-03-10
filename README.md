# Mapty – Workout Tracker on an Interactive Map

A single-page workout tracker that lets you log running and cycling sessions directly on a map. Click anywhere on the map to create a workout, store key metrics (distance, duration, pace/speed, cadence/elevation), and revisit your history with map markers and a sidebar list – all persisted in `localStorage`.

---

## ✅ Features

- **Geolocation-based map** using the browser Geolocation API (when allowed) to center the map on the user.
- **Interactive Leaflet map**: click on any location to create a workout marker.
- **Two workout types**:
  - Running – distance, duration, cadence, auto-calculated pace.
  - Cycling – distance, duration, elevation gain, auto-calculated speed.
- **Inline validation** that rejects non-numeric or negative inputs.
- **Animated form** that slides in/out above the workout list.
- **Workout list sidebar** synchronized with map markers:
  - Clicking a workout smoothly pans the map to its marker.
  - Each workout shows date, metrics, and an icon per type.
- **Persistent data** via `localStorage` so workouts remain after refresh.

---

## 🧠 What This Showcases (Frontend Skills)

This project is a good representation of my vanilla JavaScript frontend skills:

- **Modern JavaScript (ES6+)**
  - Classes and inheritance (`Workout`, `Running`, `Cycling`, `App`).
  - Private fields (`#map`, `#workouts`, etc.) and encapsulation.
  - Arrow functions, array methods (`forEach`, `find`, `every`), template literals.
- **State management without frameworks**
  - Internal app state stored in the `App` class.
  - Controlled flow from user interaction → validation → state update → DOM update → persistence.
- **DOM manipulation & events**
  - Form handling, dynamic list rendering, event delegation on the workout list.
  - Conditional UI (toggling cadence vs elevation fields based on selected type).
- **Third-party integration (Leaflet)**
  - Creating and configuring a map instance.
  - Custom markers and popups with different styles for running vs cycling.
  - Smooth panning and zooming to specific coordinates.
- **Browser APIs**
  - Geolocation API to get user position.
  - Web Storage API (`localStorage`) for persistence.
- **Layout and styling**
  - Responsive-ish two-column layout (sidebar + map) using Flexbox and CSS Grid.
  - CSS custom properties for color theming.
  - Custom popup theming for Leaflet.

If you’re a recruiter: this codebase is intentionally framework-free to demonstrate solid JavaScript fundamentals and DOM-level problem solving.

---

## 🛠 Tech Stack

- **HTML5** – semantic structure for the sidebar, form, and layout shell.
- **CSS3** – Flexbox, CSS Grid, custom properties, and component-style classes.
- **JavaScript (ES6+)** – application logic, state, and DOM interactions.
- **Leaflet.js** – lightweight open-source map library.
- **Browser APIs** – Geolocation, localStorage.

---

## 🚀 Getting Started

### 1. Clone or download

```bash
# Clone the repo
git clone <your-repo-url>
cd mapty-app
```

Or simply download the project as a ZIP and extract it.

### 2. Run locally

Because Leaflet and the Geolocation API can behave differently depending on how files are served, the safest way is to use a lightweight local server.

**Option A: VS Code Live Server (recommended)**

1. Install the **Live Server** extension in VS Code.
2. Open this folder in VS Code.
3. Right-click `index.html` and choose **"Open with Live Server"**.

**Option B: Simple Node server (if you have Node.js)**

```bash
# From the project folder
npx serve .
# or
npx http-server .
```

Then open the URL from the terminal (usually `http://localhost:3000` or `http://127.0.0.1:8080`).

### 3. Use the app

1. Allow location access when the browser asks (to center the map).
2. Click anywhere on the map.
3. Fill in the form on the left:
   - Choose **Running** or **Cycling**.
   - Enter distance and duration (and cadence or elevation gain).
4. Submit to create a workout:
   - A marker appears where you clicked.
   - A workout card is added in the sidebar.
5. Click any workout in the sidebar to pan/zoom the map to its marker.

Data is stored in `localStorage`, so refreshing the page keeps your workouts.

---

## 🧩 Code Structure

- [index.html](index.html) – page shell, sidebar markup, workout form, and map container.
- [src/css/styles.css](src/css/styles.css) – layout, palette, form styles, workout list, and Leaflet popup theming.
- [src/js/script.js](src/js/script.js) – all app logic:
  - Domain models: `Workout`, `Running`, `Cycling`.
  - Core controller: `App` class (map setup, event wiring, state, storage).
  - Rendering functions for workouts and markers.
- [assets/images/](assets/images/) – static images like logo, icon, and documentation diagrams.

The `App` class is responsible for:

- Initializing the map after geolocation succeeds.
- Listening to map clicks to show the form.
- Handling form submission, validation, and workout creation.
- Rendering workouts to both the DOM and the map.
- Persisting and restoring state from `localStorage`.

---

## 📌 Potential Improvements

If I extend this project further, here are some ideas I’d explore:

- Make the layout fully responsive on small screens (e.g., collapsible sidebar or stacked layout).
- Add the ability to **edit** or **delete** workouts.
- Show aggregate stats (total distance, total time, average pace/speed).
- Filter and sort workouts (by type, date, distance, or duration).
- Improve accessibility (focus management, ARIA attributes, keyboard-only use).
- Dark mode toggle using CSS custom properties.
