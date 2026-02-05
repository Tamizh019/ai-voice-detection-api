# 🎙️ AI Voice Detection API

Detects AI-generated vs Human voices across 5 Indian languages.

## 🚀 Quick Start

```bash
# Install dependencies
pip install -r requirements.txt

# Run the server
uvicorn main:app --reload --port 8000
```

## 📡 API Usage

### Endpoint
```
POST /api/voice-detection
```

### Headers
| Header | Value |
|--------|-------|
| Content-Type | application/json |
| x-api-key | AEGON_2050 |

### Request Body
```json
{
  "language": "Tamil",
  "audioFormat": "mp3",
  "audioBase64": "BASE64_ENCODED_AUDIO"
}
```

### Success Response
```json
{
  "status": "success",
  "language": "Tamil",
  "classification": "AI_GENERATED",
  "confidenceScore": 0.85,
  "explanation": "Unnatural pitch consistency; Low spectral variance"
}
```

### Error Response
```json
{
  "status": "error",
  "message": "Invalid API key"
}
```

## 🗣️ Supported Languages
- Tamil
- English
- Hindi
- Malayalam  
- Telugu

## 🔧 Environment Variables
| Variable | Description | Default |
|----------|-------------|---------|
| API_KEY | API authentication key | AEGON_2050 |

## 📦 Project Structure
```
AI_Voice_Detection/
├── main.py              # FastAPI application
├── audio_processor.py   # ML audio classification
├── requirements.txt     # Dependencies
├── render.yaml          # Render deployment config
├── Procfile             # Railway/Heroku config
├── .env                 # Environment variables
├── .env.example         # Env template
├── .gitignore           # Git ignore rules
└── Docs/                # Documentation
```

## 🚢 Deployment

### Render (Recommended)
1. Push code to GitHub
2. Connect Render to repo
3. Add environment variable: `API_KEY=AEGON_2050`
4. Deploy (auto-builds from render.yaml)

### Railway
```bash
railway login
railway init
railway up
railway variables set API_KEY=AEGON_2050
```

## 🧪 Testing

### Test with curl
```bash
curl -X POST http://localhost:8000/api/voice-detection \
  -H "Content-Type: application/json" \
  -H "x-api-key: AEGON_2050" \
  -d '{"language": "English", "audioFormat": "mp3", "audioBase64": "..."}'
```

### Test with provided 'test_sample'
I've included a script to automatically test the samples provided in the `test_sample` folder:

```bash
python verify_sample.py
```

This will:
1. Take `test_sample/sample voice 1.mp3`
2. Convert it to Base64
3. Send it to the API
4. Tell you if it's AI or HUMAN

### Health Check
```bash
curl http://localhost:8000/health
```

## ✅ Validation Checklist
- [x] Endpoint URL is live
- [x] x-api-key header authentication works
- [x] Accepts all 5 languages
- [x] Returns proper JSON structure
- [x] classification is "AI_GENERATED" or "HUMAN"
- [x] confidenceScore is between 0.0-1.0
- [x] explanation field is present
- [x] Error responses return proper JSON

## 🔍 How It Works
The API uses librosa for audio feature extraction:
- **MFCCs** - Spectral shape
- **Pitch variation** - AI voices have less variation
- **Spectral flatness** - AI voices are flatter
- **Zero crossing rate** - Rhythm patterns
- **RMS Energy** - Volume consistency

AI voices typically show: low spectral variance, consistent pitch, uniform energy.

## 📜 License
MIT License
