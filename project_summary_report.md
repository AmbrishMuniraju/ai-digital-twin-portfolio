# Project Summary Report: My AI-Powered Digital Portfolio

## 1. Project Overview
This project is my state-of-the-art personal portfolio website, accessible at **[ambrishmuniraju.co.uk](https://ambrishmuniraju.co.uk)**. It is designed to showcase my expertise in AI Engineering and Data Analytics. The standout feature is a fully integrated **AI Digital Twin**, a chatbot that allows visitors to have a natural conversation with a virtual version of myself, determining my suitability for roles or projects instantly.

## 2. Key Features

### 🤖 AI Digital Twin (Chatbot)
*   **Interactive Persona:** I built a custom AI agent trained on my resume and experience.
*   **Context-Aware:** It is capable of answering specific questions about my skills, past projects (e.g., "Tell me about your Crypto ETL project"), and education.
*   **Floating Access:** Accessible via a "Chat with AI" button in the Hero section and a persistent floating action button (FAB) that follows the user.

### 🎨 Modern, Responsive Design
*   **Glassmorphism UI:** I implemented premium, translucent cards with blur effects for a modern, high-tech aesthetic.
*   **Dynamic Visuals:** I added a "Spotlight" hover effect on cards and a subtle parallax scrolling effect for depth.
*   **Mobile-First Optimization:** 
    *   A custom mobile navigation drawer.
    *   Responsive layouts that adapt from complex grids (Desktop) to streamed single-column views (Mobile).
    *   Smart conditional logic (e.g., hiding duplicate buttons on mobile scroll).

### ⚡ Performance & Tech Stack
*   **Speed:** I built this on **FastAPI**, ensuring lightning-fast page loads and API responses.
*   **Styling:** I utilized **Tailwind CSS** for a lightweight, utility-first styling approach.
*   **Rendering:** Server-side rendering with **Jinja2** templates allows for dynamic content injection and SEO optimization.
*   **Live Demo:** [ambrishmuniraju.co.uk](https://ambrishmuniraju.co.uk)

## 3. Technology Stack

| Component | Technology | Purpose |
| :--- | :--- | :--- |
| **Backend** | **FastAPI (Python)** | High-performance web server & API handling. |
| **AI Engine** | **Google Gemini 2.5 Flash** | The LLM powering my digital twin. |
| **Orchestration** | **LangChain** | Managing prompts and model interaction. |
| **Frontend** | **HTML5 / Jinja2** | Semantic structure and templating. |
| **Styling** | **Tailwind CSS** | Responsive and modern styling system. |
| **Interactivity** | **Vanilla JavaScript** | handling UI events, modals, and API calls. |
| **Hosting** | **Render** | Cloud deployment platform. |

## 4. User Experience (UX) Highlights
1.  **Spotlight Effect:** Moving the mouse over "Skills" or "Experience" cards reveals a subtle lighting effect that follows the cursor, adding a premium feel.
2.  **Seamless Chat:** The chat modal opens instantly with a backdrop blur, maintaining context of the page behind it.
3.  **Smart Visibility:** I engineered the floating chat button to intelligently hide when the main "Hero" chat button is visible to avoid screen clutter.

## 5. Conclusion
This portfolio is more than just a static resume; it is a **functional demonstration of my skills**. By embedding an AI agent directly into the site, I have proven my capability as an AI Engineer in real-time to any recruiter or visitor. The clean code architecture and modern design further reinforce my attention to detail and full-stack capabilities.
