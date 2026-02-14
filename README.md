# AI-Powered Digital Portfolio & Digital Twin

[![Live Demo](https://img.shields.io/badge/Live_Site-ambrishmuniraju.co.uk-blue?style=for-the-badge&logo=googlechrome)](https://ambrishmuniraju.co.uk)
[![Tech Stack](https://img.shields.io/badge/AI-Google_Gemini_2.5-orange?style=for-the-badge)](https://deepmind.google/technologies/gemini/)
[![Backend](https://img.shields.io/badge/Backend-FastAPI-green?style=for-the-badge)](https://fastapi.tiangolo.com/)

## 📄 Project Overview
This repository documents the architecture and technical implementation of my personal portfolio website. The core feature of this project is a **"Digital Twin"**, an AI agent capable of holding real-time conversations with visitors about my professional background, skills, and projects.

Instead of a static resume, this project serves as a functional demonstration of my skills in **AI Engineering**, **Full-Stack Development**, and **System Architecture**.

**🔗 Live Website:** [ambrishmuniraju.co.uk](https://ambrishmuniraju.co.uk)

---

## 📂 Documentation & Architecture
Since the source code for this project is private, this repository hosts the technical documentation and project reports. Please review the detailed files below:

### 1. [Backend Technical Specification](./backend_tech_spec.md)
* **Architecture:** Details the integration of **Google Gemini 2.5 Flash Lite** with **LangChain** and **FastAPI**.
* **Prompt Engineering:** Explains the "Persona Definition" and context injection strategy used to ground the AI's responses.
* **Deployment:** Covers the hosting infrastructure on **Render** and security configurations.

### 2. [Project Summary Report](./project_summary_report.md)
* **UX/UI Design:** Breakdowns of the **Glassmorphism** design, spotlight effects, and mobile-first approach.
* **Features:** Overview of the interactive chat modal and dynamic content rendering.
* **Tech Stack:** A high-level summary of the frontend (Jinja2, Tailwind CSS) and backend technologies.

---

## 🛠️ Technology Stack

| Domain | Technology Used |
| :--- | :--- |
| **LLM Model** | **Google Gemini 2.5 Flash Lite** (Optimized for speed & cost) |
| **Orchestration** | **LangChain** (Context injection & prompt management) |
| **Backend** | **FastAPI** (Python 3.11+ High-performance API) |
| **Frontend** | **HTML5 / Jinja2 / Tailwind CSS** |
| **Hosting** | **Render** (Cloud Application Hosting) |

---

## 🚀 Key Features Highlights

* **Real-Time Context Injection:** The system dynamically loads my professional profile into the model's context window, eliminating the need for complex Vector RAG for this specific use case.
* **High-Performance Chat:** Leverages `async/await` processing in FastAPI to handle concurrent user requests without blocking.
* **Responsive Design:** Features a custom "Spotlight" hover effect and a fully responsive layout that adapts from complex desktop grids to streamlined mobile views.

---

*Note: This repository contains documentation and architectural specifications. The source code remains private.*
