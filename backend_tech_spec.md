# Backend Technical Specification: My AI Digital Twin Integration

## 1. Executive Summary
This document outlines the technical architecture of my AI-powered portfolio website live at **[ambrishmuniraju.co.uk](https://ambrishmuniraju.co.uk)**. The core feature is a "Digital Twin" chatbot capable of answering questions about my professional background, skills, and projects in real-time. I leveraged **Google's Gemini 2.5 Flash Lite** model via **LangChain**, hosted on **Render** using a **FastAPI** backend to build this system.

## 2. AI Architecture & Integration

### 2.1 Model Selection: Google Gemini 2.5 Flash Lite
I selected the `gemini-2.5-flash-lite` model for this implementation.

*   **Why I chose this model:**
    *   **Speed & Latency:** The "Flash" series is optimized for high-frequency, low-latency tasks, ensuring my portfolio chat feels instant and responsive.
    *   **Cost Efficiency:** It provides an excellent balance of performance and cost for my personal portfolio application compared to larger, more expensive models like GPT-4 or Gemini Pro.
    *   **Context Window:** It has a sufficient context window to hold my entire professional profile without needing complex vector retrieval (RAG) for this specific scale.

### 2.2 Framework: LangChain & FastAPI
*   **LangChain (`langchain-google-genai`):** I used this as the orchestration layer to manage the interaction with the Google Gemini API. It handles prompt templating and model communication abstraction.
*   **FastAPI:** I chose this modern, high-performance web framework for building APIs with Python 3.11+. It serves both my static frontend (via Jinja2 templates) and the dynamic `/chat` API endpoint.

### 2.3 Knowledge Retrieval Strategy (Context Injection)
Instead of a complex Vector RAG (Retrieval-Augmented Generation) system, I utilized a **Context Injection** pattern.

*   **Data Source:** I maintain a structured Markdown file (`data/profile.md`) containing my entire professional history, skills, and project details.
*   **Mechanism:**
    1.  On server startup, my application loads the correct `profile.md` content into memory.
    2.  This content is dynamically injected into the **System Prompt** of every chat request.
    3.  **Benefit:** This guarantees the AI has 100% access to all facts about me without the potential "retrieval loss" associated with vector databases. Since my profile data fits within the model's context window, this is the most accurate and robust approach.

### 2.4 Prompt Engineering Strategy
I carefully engineered the "System Prompt" to be the brain of my digital twin. It enforces a specific persona:

*   **Persona Definition:** *"You are the AI Digital Twin of Ambrish Muniraju. Speak in the first person ('I', 'me')."*
*   **Behavioral Guardrails:**
    *   Be professional, enthusiastic, and concise.
    *   Restrict answers to professional topics (skills, projects, experience).
    *   Polite fallback for unknown queries ("I'd be happy to discuss that via email").
*   **Format:** The prompt combines these behavioral instructions with the injected `{profile_data}` to create a grounded response.

## 3. Implementation Details

### 3.1 Code Structure (`main.py`)
```python
# Simplified flow of my implementation
llm = ChatGoogleGenerativeAI(model="gemini-2.5-flash-lite", ...)
profile_data = load_profile_data() # Reads my markdown file

system_prompt = """You are Ambrish's digital twin...
Here is your knowledge base: {profile_data}"""

prompt = ChatPromptTemplate.from_messages([
    ("system", system_prompt),
    ("human", "{user_query}")
])

chain = prompt | llm
```

### 3.2 API Endpoint
*   **POST `/chat`**: Accepts a JSON payload `{"query": "User question"}`.
*   **Processing:** Passes the query through the LangChain pipeline I built.
*   **Response:** Returns the AI's natural language response.

## 4. Hosting & Deployment

### 4.1 Infrastructure
*   **Platform:** Render (Cloud Hosting Platform)
*   **Service Type:** Web Service
*   **Environment:** Python 3.11

### 4.2 Configuration (`render.yaml`)
*   **Build Command:** `pip install -r requirements.txt` (Installs FastAPI, Uvicorn, LangChain, Google Gen AI SDK).
*   **Start Command:** `uvicorn main:app --host 0.0.0.0 --port $PORT` (Starts the ASGI server).
*   **Environment Variables:**
    *   `GOOGLE_API_KEY`: I securely stored my credential for accessing Gemini here.

## 5. Security & Performance
*   **Environment Variables:** My sensitive keys are never hardcoded; I inject them at runtime via `.env` (local) or Render's secret manager (production).
*   **Async Processing:** I used FastAPI's `async/await` architecture to ensure the server remains responsive even while waiting for the AI model to generate a response.
*   **CORS:** Configured to allow requests solely from my portfolio domain.

## 6. Future Scalability
If my profile data grows beyond the token limit of the "Flash" model, I designed the system to easily switch to a **Vector RAG** approach (using ChromaDB or Pinecone) by simply modifying the retrieval function in `main.py` without rewriting the frontend or API logic.
