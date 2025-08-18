# Backend Setup and Configuration
This section guides you through the modification and configuration of Foom backend.

### Backend file Structure

```
FOOM_BACKEND/
├─ core/
├─ deprecated/
├─ HF_Model/
├─ models/
├─ routes/
├─ services/
├─ third_party/
│  └─ client_secret.json         # Google OAuth 2.0 client credentials (from Google Cloud Console)
├─ utils/
├─ __init__.py
├─ .env                          # Environment variables (includes Google OAuth + app settings)
├─ backend.py                    # App factory / FastAPI-Flask backend entry (imports routes, services)
├─ model_download.py             # Model downloader (Llama-3.1-8B-instruct-GGUF)
├─ requirements.txt
└─ start.py                      # Startup script
```

<br>

#### 1. Model Download 

- First time running the backend, run the model downloader first. This will download the Llama 3.1-8B-Instruct model.

```
# cd foom_backend
python model_download.py
```

<br>

#### 2. Set Up Gemini API keys  

 - Set GOOGLE_API_KEY= in the .env file to your API key.

```
GOOGLE_API_KEY=
GEMINI_MODEL=gemini-2.5-flash
```

<br>

#### 3. Start foom backend  

For starting backend, use start.py, this will start a fastapi process

```
python start.py
```

<br>