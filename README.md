# 🏢 Workday Health Reasoning Platform (Privacy-First Desk-Worker Health Assistant)

**Pitch (1–2 lines):**  
A privacy-first, local-only health reasoning assistant for desk workers that turns daily work habits into practical, non-diagnostic recommendations, tasks, and reminders—without sending personal health data to the cloud.

---

## What Gemini 3 does in this app (~200 words)

Gemini 3 is used as an **optional reasoning engine** that transforms structured, user-provided workplace health signals into **actionable preventive guidance**. The app collects inputs across modular domains—workspace ergonomics, musculoskeletal symptoms (MSK), hydration, eye strain, productivity, sleep/recovery, and longitudinal health markers—then composes a cross-domain context from locally saved JSON records. When Gemini 3 is enabled, the model reads this context and generates a coherent set of **non-diagnostic recommendations** focused on prevention: reducing prolonged sitting, improving posture and workstation setup, managing screen habits to reduce eye strain, strengthening recovery routines, and translating insights into small, realistic actions.

Crucially, the app is designed to be **safe and judge-friendly**: it does not diagnose, it avoids medication advice, and it includes explicit “when to seek medical review” red flags. Gemini is also used to create structured outputs—like a daily action task list and time-based reminders—so the system goes beyond “tracking” and becomes a behavior-change tool. If Gemini is not available, the platform falls back gracefully, keeping the notebook runnable and the architecture demonstrable end-to-end.

---

## Key Features

- **Modular tabs**: Baseline, Workspace, MSK, Eye, Mental, Hydration, Productivity, Recovery/Sleep, Checklist, Reminders, Global Recommendations  
- **Local-only storage**: user data and AI outputs saved as JSON in the `data/` folder  
- **Context-aware reasoning**: combines signals across domains for better recommendations (e.g., screen strain + sleep + stress)  
- **Action outputs**: generates clear recommendations plus structured **tasks** and **reminder schedules**  
- **Safety guardrails**: surfaces urgent warnings and discourages diagnostic/medical treatment claims  
- **Optional AI**: Gemini 3 runs only when configured; otherwise the notebook remains functional via fallback logic  
- **Internationalization (i18n)**: designed with multilingual support (English/Arabic-ready)  

---

## How to Run

### Option A — Run the Notebook (recommended for judging)

1. Create and activate a virtual environment:
   ```bash
   python -m venv .venv
   # Windows:
   .venv\Scripts\activate
   # macOS/Linux:
   source .venv/bin/activate
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Launch Jupyter and open the notebook:
   ```bash
   jupyter lab
   # or
   jupyter notebook
   ```

4. Run cells top-to-bottom.  
   - Data is saved locally under `data/`  
   - If Gemini is configured, you’ll get AI recommendations; if not, the app uses safe fallbacks  

---

### Option B — Run the Gradio UI (if included in your project)

1. Ensure dependencies are installed (same as above).
2. Launch the app entrypoint:
   ```bash
   python app.py
   ```
3. Open the local URL shown in the terminal.

---

## Gemini 3 Configuration (Optional)

Provide your Gemini API key via environment variable:

```bash
# Windows PowerShell:
setx GEMINI_API_KEY "YOUR_KEY"

# macOS/Linux:
export GEMINI_API_KEY="YOUR_KEY"
```

Restart the terminal / Jupyter kernel after setting the variable.

---

## Data & Privacy

- All inputs and outputs are saved locally as JSON in `data/`
- No automatic uploads, no hidden telemetry
- You control what you enter and what is stored

---

## Disclaimer

This tool provides **preventive, non-diagnostic guidance** and is not a substitute for professional medical care. If you have severe symptoms or red-flag signs, seek medical attention.
