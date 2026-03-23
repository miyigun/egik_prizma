[🇹🇷 Click here for Turkish](README.tr.md)

# egik_prizma

This repository contains an **interactive, browser-based educational material** for the topic **Oblique Prism (Eğik Prizma)**.  
It is implemented as a **single-page HTML application** and includes a **3D prism viewer**, **net (unfolding) view**, and **guided activities** to support learning through exploration.

---

## Features

### 1. Interactive 3D Oblique Prism (Three.js)
- 3D model rendering with **drag to rotate** and **scroll/pinch to zoom**
- Corner labels and edge highlighting for better spatial understanding
- Reset view / rotation

### 2. Net (Unfolding) View
- Switch between **3D view** and **net view**
- Animated net presentation
- Supports coloring and learning face relationships

### 3. Measurement Tools
- **Edge length measurement** (ruler animation and displayed results)
- **Angle measurement** (select 3 vertices to measure an angle)

### 4. Face Coloring / Painting
- Color palette for painting prism faces
- Reset colors
- Net painting flow (paint net and convert back to prism visualization)

### 5. Guided Learning Flow (Activities)
- Activity-based structure (tabs in the left panel):
  - **Uygulama 1:** Identify faces and understand the net
  - **Uygulama 2:** Surface area-related tasks / assessment question
  - **Uygulama 3:** Volume-related tasks and real-life example dialogs
  - **Serbest:** Free exploration and custom interaction (available depending on flow)

### 6. Math & Content Support
- Mathematical notation rendering with **MathJax**
- Dialog-based questions and short assessments
- Uses image-based prompts from the `images/` folder

---

## Project Structure

- `index.html` — the full application (HTML/CSS/JS in one file)
- `images/` — images used in dialogs and questions (e.g., Kuril Islands, porch example, assessment figure)

---

## Getting Started

To run the app locally:

1. Clone the repository:
   ```bash
   git clone https://github.com/miyigun/egik_prizma.git
   ```

2. Go to the folder:
   ```bash
   cd egik_prizma
   ```

3. Open the app:
   - Easiest: open `index.html` in a browser
   - Recommended: run with a local server (avoids browser security restrictions)

   Example (Python):
   ```bash
   python -m http.server 8000
   ```
   Then open:
   - `http://localhost:8000`

---

## 🛠️ Technologies Used
- HTML / CSS / JavaScript
- [Three.js](https://threejs.org/) (3D rendering)
- MathJax (math notation)
- jQuery (UI/event handling)

---

## 📌 Notes
- The app is designed as a **standalone HTML file**, so there is no build step.
- Make sure the `images/` folder exists and is in the correct location for dialogs to display properly.

---

## 📜 License
This project is licensed under the MIT License. See the LICENSE file for details.