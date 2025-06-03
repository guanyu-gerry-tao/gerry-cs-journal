# Front‑End Development Overview

When you browse an online shopping site—navigating categories, comparing products—you’re interacting with the **front‑end**, built by front‑end developers using a combination of languages and tools.

---

## **1. Core Languages**

### **HTML (Structure)**

- Defines the “skeleton” of a page
- Elements include text, links, images/videos, dividers, buttons
- Ensures consistent formatting across browsers

### **CSS (Styling)**

- Adds visual design: colors, fonts, layouts
- Manages style characteristics for entire site and individual components
- Ensures cross‑browser and cross‑device compatibility (PC, mobile, tablet)

### **JavaScript (Interactivity)**

- Object‑oriented language working alongside HTML & CSS
- Adds dynamic behavior (e.g., login button functionality)
- Improves user experience with quick, interactive features

---

## **2. CSS Preprocessors**

CSS preprocessors are tools that **extend** CSS with additional features like variables, nested rules, and imports, making stylesheet creation faster and more organized. They compile into standard CSS that browsers can understand.

SASS 和 LESS 都是 CSS 的预处理器，用来增强 CSS 的表达能力。样式多、结构深、主题复杂、需要复用时，纯 CSS 就会显得笨重；SASS / LESS 提供**变量、嵌套、复用、模块化**

- **SASS (Syntactically Awesome Style Sheets)**
    - Extension of CSS, fully compatible
    - **Supports variables, nested rules, inline imports**
    - Speeds up and organizes stylesheet creation
- **LESS (Learner Style Sheets)**
    - **Enhances CSS with additional features**
    - Backwards‑compatible
    - Converted to CSS via Less.js

---

## **3. Adaptive vs. Responsive Design**

- **Adaptive (Reactive) Websites**
    - Serve different layouts optimized for specific screen sizes
    - E.g., richer interface on PC, simplified on mobile
- **Responsive Websites**
    - Automatically resize and reflow content to fit any viewport
    - Maintain full feature set across devices

---

## **4. JavaScript Frameworks & Libraries**

- **Angular** (Google‑maintained)
    - Full‑featured framework
    - Fast HTML rendering, built‑in routing & form validation
- **React.js** (Facebook‑maintained)
    - Library for building UI components
    - Not a complete framework—requires third‑party routing
- **Vue.js** (Community‑maintained)
    - Focus on “view” layer (UI components)
    - Flexible: can be a library or full framework
    - Easy integration with other tools