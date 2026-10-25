# CrimeVision AI

**Intelligent Multimodal Forensic Analysis Platform**
Skill Wallet Capstone Project 2

CrimeVision AI is a Streamlit app that helps investigators analyze crime scene evidence across images, audio and video, then combines everything into one case view and exports a forensic PDF report. LLM features run on Groq (Llama 3.3 70B and Whisper Large v3).

## Features

| Tab | What it does |
|---|---|
| **Image Analysis** | Upload a scene photo, get labeled detections (weapons, blood spatter, forced entry, etc.), a threat level, scene classification, an AI narrative and investigative leads. Includes a 3D scene reconstruction view. |
| **Audio Analysis** | Upload a call or witness recording, transcribe it with Whisper, and turn it into a timestamped event timeline ranked by significance. |
| **Video Analysis** | Upload CCTV footage, sample key frames with OpenCV, classify events by crime category, and chart how the incident progresses. |
| **Evidence Fusion** | Master evidence ledger, a combined timeline across all sources, and a forensic chat assistant that answers questions using the collected evidence. |
| **PDF Report** | Generates a full case report with an AI executive summary, ready to download. |

Every piece of evidence gets a unique ID and a SHA-256 chain-of-custody record.

## Tech Stack

- **Frontend / App:** Streamlit, Plotly
- **AI:** Groq API (`llama-3.3-70b-versatile`, `whisper-large-v3`)
- **Media processing:** OpenCV, Pillow, NumPy
- **Reports:** ReportLab
- **Data:** Pandas

## Project Structure

```
crimevision/
├── app.py                  # Main Streamlit entry point
├── config/
│   └── settings.py         # Constants, threat levels, custody hashing, demo data
├── modules/
│   ├── image_analysis.py
│   ├── audio_analysis.py
│   ├── video_analysis.py
│   ├── fusion.py
│   └── pdf_report.py
├── utils/
│   ├── groq_client.py      # All Groq LLM + Whisper calls
│   ├── evidence_store.py   # Session evidence storage
│   └── ui_helpers.py       # Custom CSS and UI components
├── requirements.txt
├── run_app.bat
└── .env.example
```

## Getting Started

**1. Clone the repo**
```bash
git clone https://github.com/Heenaljain21/crimevision.git
cd crimevision
```

**2. Create a virtual environment and install dependencies**
```bash
python -m venv venv
venv\Scripts\activate        # Windows
source venv/bin/activate     # macOS / Linux
pip install -r requirements.txt
```

**3. Add your Groq API key**

Copy `.env.example` to `.env` and paste your key (free at [console.groq.com](https://console.groq.com)):
```
GROQ_API_KEY=your_groq_api_key_here
```
You can also enter the key in the app sidebar.

**4. Run the app**
```bash
streamlit run app.py
```
Or on Windows, just double-click `run_app.bat`. The app opens at http://localhost:8501.

## Demo Mode

No API key? The app still runs in demo mode with built-in sample data (a scene analysis, a 911 call transcript and CCTV events), so you can explore every tab without setting anything up.

## Notes

- Object detection in the image module is currently simulated to demonstrate the pipeline. Plugging in a real detection model (e.g. RT-DETR) is the next step.
- This is an academic project and is not intended for real forensic or legal use.

## Author

**Heenal Jain** · [GitHub](https://github.com/Heenaljain21)
