---
title: AI Voice Detection
emoji: 🌍
colorFrom: gray
colorTo: pink
sdk: docker
pinned: false
---

# 🎤 AI Voice Detection API (For Hackathon)

> **Detect AI-generated voices with confidence**  
> A FastAPI-powered solution for identifying synthetic speech across 5 languages

[![Hugging Face](https://img.shields.io/badge/🤗%20Hugging%20Face-Spaces-blue)](https://huggingface.co/spaces/Tamizh019/AI_Voice_Detection)
[![Python](https://img.shields.io/badge/Python-3.12-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.109-green.svg)](https://fastapi.tiangolo.com/)

---

## Our Team

- **Ajay**
- **Tamizharasan**
- **Varshini Sekar**
- **Faheem**

---

## 🚀 Live Demo

**API Endpoint:** `https://tamizh019-ai-voice-detection.hf.space/api/voice-detection`

### ⚡ Quick Test
We have provided sample Base64 files for you!
1. Open `samples/human_sample(Base64).txt` (or `samples/AI_sample(Base64).txt`)
2. Copy the **entire content**
3. Paste it into `audioBase64` below:

```bash
curl -X POST https://tamizh019-ai-voice-detection.hf.space/api/voice-detection \
  -H "Content-Type: application/json" \
  -H "x-api-key: YOUR_API_KEY" \
  -d '{
    "language": "English",
    "audioFormat": "mp3",
    "audioBase64": "PASTE_CONTENT_FROM_TXT_FILE_HERE"
  }'
```

---

## 🟠 Testing with Postman

If you prefer a GUI tool like Postman:

1. **Create New Request**: Set method to `POST`
2. **URL**: `https://tamizh019-ai-voice-detection.hf.space/api/voice-detection`
3. **Headers Tab**:
   - `Content-Type`: `application/json`
   - `x-api-key`: `YOUR_API_KEY`
4. **Body Tab** (Select `raw` -> `JSON`)

**Paste this template:**
```json
{
  "language": "English",
  "audioFormat": "mp3",
  "audioBase64": "PASTE_CONTENT_HERE"
}
```

**Where to get the content?**
- **For Human Test:** Open `samples/human_sample(Base64).txt` and copy everything.
- **For AI Test:** Open `samples/AI_sample(Base64).txt` and copy everything.

---

## 🛠️ Need Custom Audio?

If you find it hard to convert your own mp3 files to Base64, we included a helper script!

1. **Install Python** (if not installed)
2. **Run this command** in your terminal:

```bash
python utils/generate_base64.py "path/to/your/audio.mp3"
```

It will print the Base64 string for you to copy! 🚀

---

## ✨ Features

- 🎯 **Accurate Detection** - Rule-based heuristics tuned for modern AI voices
- 🌍 **Multi-Language** - Supports Tamil, English, Hindi, Malayalam, Telugu
- ⚡ **Fast Response** - Results in 2-5 seconds
- 🔒 **Secure** - API key authentication
- 📊 **Confidence Scoring** - 0.0 to 1.0 confidence with explanations
- 🚫 **No Hardcoding** - Real audio analysis using librosa

---

## 📖 Quick Start

### Used Technical Stack

- **Backend:** FastAPI, Uvicorn
- **Audio Processing:** librosa, pydub, soundfile
- **ML:** NumPy, SciPy, numba
- **Deployment:** Hugging Face Spaces (Docker)
- **Security:** Environment-based API key auth

---

## 📂 Project Structure

```
AI_Voice_Detection/
├── main.py                 # FastAPI application
├── core/                   # Core logic
│   └── audio_processor.py  # ML feature extraction & classification
├── utils/                  # Utility scripts
│   ├── generate_base64.py  # Audio → Base64 converter
│   └── keep_alive.py       # Keep HF Space awake
├── samples/                # Sample data
│   ├── AI_sample(Base64).txt
│   └── human_sample(Base64).txt
├── tests/                  # Testing scripts
│   └── verify_sample.py    # Verify deployment
├── Docs/                   # Documentation
└── requirements.txt        # Dependencies
```

---

## 📊 API Reference

### Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/voice-detection` | POST | Classify audio as AI or Human |
| `/health` | GET | Health check |
| `/` | GET | API information |

### Authentication

All requests require the `x-api-key` header:
```
x-api-key: YOUR_API_KEY
```

### Supported Languages
- Tamil
- English
- Hindi
- Malayalam
- Telugu

📚 **Complete API Docs:** [API_GUIDE.md](./Docs/API_GUIDE.md)

---

**Built with ❤️ for the AI Voice Detection Hackathon**
