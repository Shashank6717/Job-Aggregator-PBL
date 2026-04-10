# 🚀 JobSage.ai: Your Agentic Career Companion

JobSage.ai is a next-generation, AI-powered job search and career assistant. By combining **LangGraph** orchestration with real-time **LLM Streaming**, JobSage.ai transforms the fragmented job search experience into a seamless, conversational journey.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.12+](https://img.shields.io/badge/python-3.12+-blue.svg)](https://www.python.org/downloads/)
[![Node.js 18+](https://img.shields.io/badge/node.js-18+-green.svg)](https://nodejs.org/)

---

## 📋 Table of Contents

- [✨ Key Features](#-key-features)
- [🛠️ Tech Stack](#️-tech-stack)
- [🚀 Getting Started](#-getting-started)
- [🔧 Installation](#-installation)
- [⚙️ Configuration](#️-configuration)
- [📖 Usage](#-usage)
- [📄 License](#-license)

---

## ✨ Key Features

### � **MCP-Powered Job Search** 🚀

- **Model Context Protocol Integration**: Seamlessly connects to LinkedIn and other platforms through MCP servers
- **Unified API Access**: Single interface to access multiple job platforms without complex authentication
- **Real-time Data Streaming**: Live job data updates through MCP protocol for the freshest opportunities

### 🗣️ Natural Language Search & Discovery

- **Intent Recognition**: Uses a high-context router to distinguish between general career advice and active job intent
- **Smart Parsing**: Automatically extracts `keywords`, `location`, `skills`, `experience_level`, and `work_mode` from unstructured text
- **Multi-Source Aggregation**: Diversified results from LinkedIn (**MCP servers**), Indeed (via Tavily), Naukri, and other job platforms

### 🎙️ Voice-First Interaction

- **Transcription (STT)**: Uses `faster-whisper` with `whisper-int8` for fast, local conversion of voice messages to text
- **Speech Synthesis (TTS)**: Integration with **Piper TTS** for ultra-fast, offline-capable spoken responses
- **Voice Condensation**: Dynamically summarizes long AI responses into concise chunks specifically optimized for audio playback

### ⚡ Performance & Streaming

- **True Direct Streaming**: Employs LangChain `astream_events` (v2) to bypass traditional API latencies, delivering tokens directly from the model as they are generated
- **Fluid UI Transition**: Automatically toggles between `auto` and `smooth` CSS scroll behavior during streaming to eliminate layout stuttering

### 🧠 Personalization & Intelligence

- **Skill-Based Ranking**: Ranks every job listing against your unique tech stack or uploaded resume
- **Structured Extraction**: Gemini 1.5/2.0 powered scrapers that turn messy job pages into clean Markdown tables and rich UI cards
- **Automatic Fallbacks**: If a listing site is sparse, the system inferencing engine generates a 2-sentence summary of the role automatically

### 🎨 Modern UI/UX

- **Neo-Brutalism Design**: High-contrast borders, vibrant accents, and bold drop-shadows for a distinctive look
- **Responsive Design**: Optimized for desktop, tablet, and mobile devices
- **Dark/Light Mode**: Automatic theme switching based on user preferences

---

## 🛠️ Tech Stack

### 🔗 **MCP Integration**

- **Model Context Protocol**: Standardized interface for connecting to external data sources
- **LangChain MCP Adapters**: Seamless integration with MCP servers for job platform access
- **MCP Server Implementation**: Custom MCP servers for LinkedIn and other job platforms

### Backend

- **Python 3.12+**
- **FastAPI**: High-performance async web framework
- **LangGraph**: For building robust AI agents with state machines
- **LangChain**: LLM orchestration and streaming with **MCP support**
- **Groq API**: Fast inference for real-time responses
- **Google Gemini**: Structured data extraction and ranking
- **Tavily**: Real-time web search
- **Firecrawl**: Web scraping and data extraction
- **Faster Whisper**: Speech-to-text transcription
- **Piper TTS**: Text-to-speech synthesis

### Frontend

- **Next.js 16**: React framework with App Router
- **TypeScript**: Type-safe JavaScript
- **Tailwind CSS**: Utility-first CSS framework
- **Framer Motion**: Animation library
- **React Markdown**: Markdown rendering with GFM support
- **Supabase**: Real-time database and authentication

### Infrastructure

- **Supabase**: PostgreSQL database with real-time subscriptions
- **Uvicorn**: ASGI server for FastAPI
- **Docker**: Containerization (optional)

### Development Tools

- **uv**: Fast Python package manager
- **ESLint**: JavaScript/TypeScript linting
- **Prettier**: Code formatting

---

## 🚀 Getting Started

### Prerequisites

- Python 3.12 or higher
- Node.js 18 or higher
- uv (recommended for faster Python package management)
- Git

### Quick Start

1. **Clone the repository**

   ```bash
   git clone https://github.com/Shashank6717/Job-Aggregator-PBL.git
   cd job-aggregator-main
   ```

2. **Set up the backend**

   ```bash
   # Install Python dependencies
   uv sync

   # Copy environment file and configure
   cp .env.example .env
   # Edit .env with your API keys
   ```

3. **Set up the frontend**

   ```bash
   cd frontend
   npm install
   cp .env.local.example .env.local
   # Edit .env.local with your Supabase credentials
   ```

4. **Run the application**

   ```bash
   # Terminal 1: Start the backend
   uv run uvicorn server:app --reload --port 4000

   # Terminal 2: Start the frontend
   cd frontend
   npm run dev
   ```

5. **Open your browser**
   Navigate to `http://localhost:3000`

---

## 🔧 Installation

### Backend Setup

1. **Install uv (if not already installed)**

   ```bash
   # On Windows
   winget install astral-sh.uv

   # Or using pip
   pip install uv
   ```

2. **Install dependencies**

   ```bash
   uv sync
   ```

3. **Set up environment variables**
   Create a `.env` file in the root directory:
   ```env
   GROQ_API_KEY=your_groq_api_key
   GOOGLE_API_KEY=your_google_api_key
   TAVILY_API_KEY=your_tavily_api_key
   SUPABASE_URL=your_supabase_url
   SUPABASE_KEY=your_supabase_key
   ```

### Frontend Setup

1. **Install Node.js dependencies**

   ```bash
   cd frontend
   npm install
   ```

2. **Configure environment**
   Create `.env.local` in the frontend directory:
   ```env
   NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
   NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
   ```

### Database Setup

1. **Create a Supabase project**
   - Go to [supabase.com](https://supabase.com)
   - Create a new project
   - Get your project URL and anon key

2. **Set up database tables**
   The application will automatically create the necessary tables on first run.

---

## ⚙️ Configuration

### Environment Variables

#### Backend (.env)

- `GROQ_API_KEY`: API key for Groq (required for LLM inference)
- `GOOGLE_API_KEY`: API key for Google Gemini (required for structured extraction)
- `TAVILY_API_KEY`: API key for Tavily (required for web search)
- `SUPABASE_URL`: Supabase project URL (required for data persistence)
- `SUPABASE_KEY`: Supabase service role key (required for data persistence)

#### Frontend (.env.local)

- `NEXT_PUBLIC_SUPABASE_URL`: Supabase project URL
- `NEXT_PUBLIC_SUPABASE_ANON_KEY`: Supabase anon key

### Optional Configuration

- **Whisper Model**: Configure the Whisper model size in `server.py`
- **Piper Voice**: Change the TTS voice by modifying `piper_model_path`
- **Search Sources**: Enable/disable job sources in `config.py`

---

## 📖 Usage

### Basic Job Search

1. **Text Search**: Type a natural language query like "Find Python developer jobs in San Francisco"
2. **Voice Search**: Click the microphone button and speak your query
3. **Resume Upload**: Upload your resume for personalized job ranking

### Advanced Features

- **Skill Matching**: Jobs are automatically ranked based on your skills
- **Location Filtering**: Specify preferred locations in your query
- **Experience Level**: Mention seniority level (junior, senior, etc.)
- **Work Mode**: Specify remote, hybrid, or on-site preferences

### Chat Interface

- **Persistent Conversations**: All chats are saved and can be resumed
- **Streaming Responses**: See AI responses as they're generated
- **Voice Responses**: Listen to AI responses with TTS

---
## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---
**Made with ❤️ for job seekers everywhere**
