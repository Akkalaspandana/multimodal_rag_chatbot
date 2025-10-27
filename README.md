# 🧠 Multi-Media Chat Bot

## 🎯 What is My Project?

We built a **Multi-Media Chat Bot** — an intelligent assistant that can understand and respond to different types of content including text, PDFs, images, and audio files.

Unlike traditional chatbots that only handle text, our bot can:

- **Read and analyze PDF documents** — Ask questions about uploaded PDFs  
- **See and understand images** — Describe what's in uploaded pictures  
- **Listen to audio files** — Transcribe and answer questions about audio content  
- **Chat naturally** — Have conversations while remembering context  
- **Speak back** — Convert responses to audio for better user experience  

---

## 🏗️ How We Built It

### Our Technical Approach

We created a **multimodal RAG (Retrieval-Augmented Generation)** system that combines:

- **Local AI models** (no cloud dependency)  
- **Vector databases** for storing and retrieving information  
- **Multiple processing pipelines** for different content types  
- **Smart context management** for meaningful conversations  

---

### Our Implementation Strategy

#### 1. **Frontend Interface (Streamlit)**
- Built a clean, user-friendly web interface  
- File upload system for PDFs, images, and audio  
- Real-time chat interface with message history  
- Toggle switches for different modes (PDF chat, etc.)

#### 2. **AI Brain (Ollama + Llama3.2)**
- Used **Ollama** to run **Llama3.2:3b** model locally  
- No internet dependency for AI processing  
- Configured with optimal temperature (0.75) for balanced responses  
- GPU acceleration for faster processing  

#### 3. **Memory System (Chroma Vector Database)**
- **Chroma** for storing document embeddings locally  
- Automatic fallback from Pinecone to Chroma (no API keys needed)  
- Smart document chunking (512 characters with 64 overlap)  
- Context retrieval for relevant information  

#### 4. **Audio Processing Pipeline**
- **FFmpeg** for audio format conversion (to 16kHz mono WAV)  
- **Google Speech Recognition** for audio-to-text  
- **gTTS** for text-to-speech responses  
- Automatic cleanup of temporary files  

#### 5. **Document Processing**
- **PyPDF2** for PDF text extraction  
- **RecursiveCharacterTextSplitter** for smart document chunking  
- **OllamaEmbeddings** for creating document vectors  
- **SQLRecordManager** for tracking processed documents  

#### 6. **Image Understanding**
- **Visual Question Answering (VQA)** system  
- Image analysis and description capabilities  
- Integration with the main chat flow  

---

## 🔧 Our Development Process

### Step 1: **Core Architecture Setup**
- Set up **Streamlit** as the web interface  
- Integrated **LangChain** for LLM orchestration  
- Configured **Ollama** with Llama3.2:3b model  
- Set up **Chroma** vector database for local storage  

### Step 2: **Multimodal Processing Implementation**
- **PDF Processing**: Built pipeline to extract, chunk, and embed PDF content  
- **Audio Processing**: Integrated FFmpeg for audio conversion and speech recognition  
- **Image Processing**: Added VQA capabilities for image understanding  
- **Text Processing**: Implemented conversation memory and context management  

### Step 3: **Smart Integration**
- Created **dual-chain system**: Regular chat vs RAG-enabled chat  
- Implemented **context-aware retrieval** for relevant document chunks  
- Added **conversation history** for follow-up questions  
- Built **file management system** with automatic cleanup  

### Step 4: **User Experience Optimization**
- **File upload handling** with proper validation  
- **Real-time processing** with progress indicators  
- **Audio responses** for better accessibility  
- **Error handling** and user feedback systems  

---

## 🎯 Key Features We Implemented

### **Smart Question Handling**
- **Context-Aware Responses**  
- **Follow-up Questions** for natural dialogue  
- **Multi-Modal Integration** for seamless content understanding  

### **Advanced Processing Capabilities**
- **PDF Intelligence** for smart retrieval  
- **Audio Understanding** with transcription  
- **Visual Analysis** using VQA  
- **Conversation Memory** for coherent dialogue  

### **User Experience Features**
- **Real-time Processing** with indicators  
- **Audio Responses** using gTTS  
- **File Management** with auto cleanup  
- **Error Handling** for smooth recovery  

---

## 🚀 How to Run Our Project

### Quick Start
```bash
# Install dependencies
pip install -r requirements.txt

# Install FFmpeg (for audio processing)
# Windows: choco install ffmpeg
# Linux: sudo apt install ffmpeg
# macOS: brew install ffmpeg

# Install and start Ollama
ollama pull llama3.2:3b
ollama serve

# Run the application
streamlit run app.py
