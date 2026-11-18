# 🎙️ AI Meeting Assistant & Intelligence System

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.35+-FF4B4B?style=flat&logo=streamlit&logoColor=white)](https://streamlit.io/)
[![LangChain](https://img.shields.io/badge/LangChain-LCEL-000000?style=flat)](https://www.langchain.com/)
[![Mistral AI](https://img.shields.io/badge/LLM-Mistral-FD6F00?style=flat)](https://mistral.ai/)
[![Whisper](https://img.shields.io/badge/ASR-OpenAI_Whisper-00A67E?style=flat&logo=openai&logoColor=white)](https://github.com/openai/whisper)
[![Vector Store](https://img.shields.io/badge/Vector_DB-ChromaDB-6A0DAD?style=flat)](https://www.trychroma.com/)

An end-to-end AI-powered meeting companion that ingests audio/video (local files or YouTube URLs), performs local multi-lingual speech-to-text transcription, generates structured summaries, and provides an interactive Retrieval-Augmented Generation (RAG) interface to chat with meeting transcripts.

---

## ✨ Features

- 📥 **Flexible Audio Extraction:** Download audio directly from YouTube URLs (`yt-dlp`) or upload local audio/video files.
- 🔊 **Audio Preprocessing:** Format normalization, segment chunking, and conversion via `pydub` and `ffmpeg`.
- 🗣️ **Local Speech-to-Text:** High-accuracy offline transcription powered by **OpenAI Whisper** (runs on CPU/GPU via PyTorch).
- 🌐 **Translation Support:** Automatic Hindi-to-English (and multi-language) translation pipelines.
- 🧠 **Smart Summarization:** Generates executive summaries, key decisions, and action items using **Mistral AI** via LangChain LCEL.
- 💬 **RAG-Powered Meeting Q&A:** Vector search powered by **ChromaDB** and **HuggingFace Sentence Transformers** for grounded contextual answering.
- 📄 **Export Capabilities:** One-click export of transcripts, summaries, and action points to **PDF** and **TXT**.
- 💻 **Interactive UI:** Clean, reactive dashboard built with **Streamlit**.

---

## 🏗️ System Architecture

```text
[ YouTube URL / Local Audio ]
              │
              ▼
    [ extractor.py ] ──> [ audio_processor.py ] (FFmpeg / pydub)
                                  │
                                  ▼
                        [ transcriber.py ] (Whisper Local ASR)
                                  │
                   ┌──────────────┴──────────────┐
                   ▼                             ▼
        [ summarizer.py ]              [ vector_store.py ]
      (Mistral Key Insights)          (Sentence Transformers + ChromaDB)
                   │                             │
                   │                             ▼
                   │                     [ rag_engine.py ]
                   │                  (Contextual Chat / LCEL)
                   └──────────────┬──────────────┘
                                  ▼
                        [ app.py / main.py ] (Streamlit UI / CLI)
                                  │
                                  ▼
                         [ PDF / TXT Export ]
## repo structure

├── .gitignore             # Ignored files, virtual environments, and cache
├── requirements.txt       # Project dependencies
├── app.py                 # Streamlit web application frontend
├── audio_processor.py     # Audio manipulation, slicing, and conversion
├── extractor.py           # Ingestion logic for YouTube/URLs and uploads
├── main.py                # Core orchestration script / CLI entrypoint
├── rag_engine.py          # RAG pipeline logic and LangChain LCEL chains
├── summarizer.py          # Meeting summarization and action items extractor
├── test.py                # Unit and integration tests
├── transcriber.py         # Whisper ASR transcription & translation
└── vector_store.py        # ChromaDB setup and embedding management

