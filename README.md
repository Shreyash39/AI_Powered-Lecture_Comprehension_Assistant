# LearnWise - AI Powered Lecture Comprehension Assistant  


Transform passive video watching into an active, efficient, and personalized learning session.  
**LearnWise** automatically transcribes lectures, generates structured notes, creates practice questions, and provides an interactive Q&A system—powered by state-of-the-art AI.  

**Developer**: Shreyash Chaudhari | Mathematics and Computing Engineering | Indian Institute of Technology, Goa  
**Email**: chaudhari.shreyash.23033@iitgoa.ac.in  
📖 Detailed Project Report & Documentation: *[Google Doc](https://docs.google.com/document/d/11Jw8jD41AUCCjvoVR8yyDhxjsBOhrKEf_ZUqIaaRN6E/edit?tab=t.0#heading=h.8pgxc6j30ni8)*  
---

## ✨ Features  

- 🎤 **Accurate Transcription**: Leverages OpenAI's Whisper model for high-quality speech-to-text conversion.  
- 📝 **Smart Note Generation**: Uses fine-tuned LLaMA models to create well-structured study notes with LaTeX rendering.  
- ❓ **AI-Generated Quizzes**: Creates MCQs and application-based questions with answers and rationales.  
- 💬 **Interactive Q&A Chat**: RAG-powered Explainer Agent provides concise, cited answers.  
- 📊 **Model Benchmarking**: Built-in WER evaluation using the TED-LIUM dataset.  
- ⚡ **Real-Time UI**: Modern React frontend with live WebSocket updates.  
- 🤖 **Multi-Model Support**: LLaMA-3 (8B/70B), Mistral, and CodeLLaMA optimized for tasks.  

---

## 🏗️ System Architecture  

LearnWise is built on a modern, agent-based architecture for flexibility and performance.  
<!-- Image will be placed here -->

## 📁 Project Structure  

```text
LearnWise/
├── backend/                   # Python FastAPI Backend
│   ├── agents/                # AI Agent Modules
│   │   ├── __init__.py
│   │   ├── transcriber.py     # Handles audio transcription (Whisper)
│   │   ├── summarizer.py      # Generates notes from transcripts
│   │   ├── quiz.py            # Creates quiz questions (Complex prompt engineering)
│   │   ├── explainer.py       # Powers the Q&A system (RAG implementation)
│   │   └── tedlium_eval.py    # Runs WER evaluation benchmark
│   ├── rag/                   # Retrieval-Augmented Generation System
│   │   ├── __init__.py
│   │   └── ingest.py          # Chunks and indexes text for semantic search
│   ├── bus.py                 # Pub/Sub message bus for inter-agent communication
│   ├── registry.py            # Manages session state and model clients
│   ├── my_llm.py              # Abstraction layer for LLMs (Local + HF Inference)
│   ├── app.py                 # Main FastAPI application and HTTP gateway
│   └── requirements.txt       # Python dependencies
├── frontend/                  # React Vite Frontend
│   ├── src/
│   │   ├── App.jsx            # Main React component (State management & WebSockets)
│   │   ├── main.jsx           # App entry point
│   │   ├── styles.css         # Comprehensive custom CSS (No Tailwind)
│   │   └── ...
│   ├── package.json
│   └── vite.config.js
└── README.md
``` 
## 🚀 Running the Application  

You need to run both the backend server and the frontend development server.  

### Terminal 1: Start the Backend (FastAPI)  
```bash
cd backend
source venv/bin/activate  # Activate your virtual environment
uvicorn app:app --reload --host 0.0.0.0 --port 8000
```
## 🚀 Terminal 2: Start the Frontend (React)

```bash
cd frontend
npm run dev
```
The application will be available at: [http://localhost:5173](http://localhost:5173)

---

## 🎯 How to Use

1. **Open the App:** Go to [http://localhost:5173](http://localhost:5173) in your browser.  
2. **Select a Model:** Choose an AI model from the dropdown (e.g., *LLaMA-3-8B* for a good balance of speed and quality).  
3. **Provide Content:**  
   - **Option A (Video):** Paste a YouTube URL into the input field.  
   - **Option B (Document):** Click **"PDF/Slides"** tab and upload a textbook chapter, slides (**PDF, PPTX**), or notes (**TXT**).  
4. **Process:** Click **"Process with [Model Name]"**. Watch the real-time transcription flow in!  
5. **Explore:** Switch between the tabs to see:  
   - **Transcript:** The full, timestamped text.  
   - **Smart Notes:** Beautifully formatted summary with headings and equations.  
   - **Quiz Questions:** Test yourself with generated MCQs and application problems.  
   - **AI Chat:** Ask any question about the material in the chat box.  
6. **(Optional) Run Evaluation:** Go to the **"WER"** tab in the sidebar to run a benchmark of the Whisper model on the **TED-LIUM dataset** and see detailed accuracy metrics.  

---

## 🔧 Configuration

Key configuration is handled through environment variables:

| Variable       | Description                                      | Default               |
|----------------|--------------------------------------------------|-----------------------|
| `HF_TOKEN`     | Your Hugging Face API token for model access     | -                     |
| `VITE_API_BASE`| Base URL of the backend API (set in `frontend/.env`) | http://127.0.0.1:8000 |

Model settings can be modified in `backend/my_llm.py` under the **`MODEL_MAP`** dictionary.  

---

## 📊 Evaluation & Results

This project includes a rigorous evaluation module. Key results:

- **Transcription Accuracy:** Whisper-small achieves a ~**12.5% Word Error Rate (WER)** on the standard TED-LIUM benchmark.  
- **Quiz Quality:** Human evaluation shows ~**80%** of generated questions are relevant, accurate, and pedagogically useful.  
- **Summary Quality:** Generated notes achieve ~**85%** coverage and clarity compared to human-made notes.  

See the detailed report in the Google Doc for full methodology and analysis.  

---

## 🚧 Future Work

- Fine-tune Whisper on multilingual (e.g., Indian-accented English) lectures.  
- Implement instruction fine-tuning for LLaMA on educational content.  
- Add user authentication and personal history.  
- Develop a spaced repetition system for generated quizzes.  
- Support for more real-time processing features.  

---

## 👨‍💻 Developer

**Shreyash Chaudhari**  
Mathematics and Computing Engineering  
Indian Institute of Technology, Goa  
📧 chaudhari.shreyash.23033@iitgoa.ac.in  

This project was developed to solve the real-world problem of efficiently consuming vast amounts of online lecture content (like NPTEL videos) for exam preparation at IIT Goa.  

---

## 📜 License

This project is licensed under the **MIT License** – see the [LICENSE](./LICENSE) file for details.  

---

## 🙏 Acknowledgments

- **Hugging Face** for providing access to powerful open-source models.  
- The **TED-LIUM consortium** for the benchmark dataset.  
- The open-source communities behind **FastAPI, React, Whisper, and LLaMA**.  

---

⭐ If you find this project helpful, please give it a **star** on GitHub!


