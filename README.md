# 🏥 CareSync (CareApp) — Smart AI Caregiving & Patient Health Ecosystem

**CareSync** is an intelligent, compassionate eldercare coordination platform connecting families with background-verified professional caregivers. Designed to bridge the communication gap between family guardians and on-duty health aides, CareSync couples **continuous biometric health telemetry** and **Gemini-powered Clinical NLP** with **geofenced, selfie-based two-factor authentication (2FA)** to guarantee verifiable, accountable, and transparent home care.

---

<!-- STREAMING_CHUNK:Documenting project highlights and core problem space -->
## 🌟 Core System Highlights

### 1. 📸 Selfie 2FA Activity Tracking & Geofenced Presence Ledger
- **Biometric Proof of Care**: Caregivers authenticate milestone completion (shift check-in, medication dispensation, mobility exercises, meals) by capturing a selfie verification photo.
- **Hardware Integration**: Directly interfaces with device cameras via `navigator.mediaDevices.getUserMedia` with fallback simulated canvas badges.
- **Tamper-Evident Geofencing**: Every check-in is stamped with real-time timestamps and GPS coordinates (e.g., *Oak Ridge Res. 40.7128° N, 74.0060° W*) to reassure remote family members that care is actively occurring on-site.

<!-- STREAMING_CHUNK:Describing the Clinical NLP Scribe engine -->
### 2. 🎙️ Clinical NLP Consultation Scribe (Powered by Gemini)
- **Speech-to-Clinical Dictation**: Integrated `webkitSpeechRecognition` engine allows caregivers and attending physicians to dictate stream-of-consciousness consultation notes hands-free.
- **Automated SOAP Structuring**: Gemini parses unstructured clinical dictations into formal **SOAP** components:
  - **S (Subjective)**: Patient symptoms and self-reported complaints.
  - **O (Objective)**: Observed physical signs, vital measurements, and pedal edema.
  - **A (Assessment)**: Clinical diagnosis synthesis and trend evaluations.
  - **P (Plan)**: Dietary, exercise, and caregiver action items.
- **Medication Entity Extraction**: Automatically isolates dosage alterations (e.g., *Lisinopril 10mg daily*, *Metformin 500mg with dinner*) and prompts one-click scheduling for follow-up doctor appointments.
- **Deterministic Heuristic Fallback**: Operates smoothly offline with a built-in clinical entity parser when network or API keys are unavailable.

<!-- STREAMING_CHUNK:Detailing biometrics radar and health telemetry -->
### 3. 📈 Continuous 7-Day Biometric Trend & Anomaly Radar
- **HTML5 Canvas Telemetry**: Responsive multi-metric visualization comparing Systolic Blood Pressure, Diastolic Blood Pressure, and Resting Heart Rate.
- **Clinical Target Zone Bands**: Visually highlights safe baseline physiological corridors (110–130 mmHg) to catch spikes and abnormal variations.
- **AI Daily Health Synthesis**: Generates conversational, jargon-free health updates for family circles with actionable preventative recommendations.
- **Interactive ADL Checklist**: Tracks daily activities of daily living (morning vitals, nutrition, hydration milestones, physical therapy).

<!-- STREAMING_CHUNK:Documenting verified caregiver directory and communication hub -->
### 4. 🛡️ Verified Professional Caregiver Directory
- **Vetted Credential Audits**: Provider listings indexed with verified state RN/CNA license numbers, FBI background clearance, CPR certification, and clinical experience.
- **Specialty Filtering**: Filter caregivers by acute senior care specialties:
  - 🧠 *Dementia & Memory Care* (CDP Certified)
  - 🚶 *Post-Surgery & Mobility / Physical Therapy*
  - ❤️ *Cardiovascular & Geriatric Rehabilitation*
- **Instant Shift Assignment**: Dispatch requests to vetted caregivers based on patient needs.

### 5. 👥 Dual-Persona Switcher & Family Care Circle
- **Family Guardian vs. Caregiver Portals**: Toggle instantly between an intuitive family dashboard and an operational clinical chart view.
- **Real-Time Care Circle Chat**: Synchronous messaging hub for family relatives and active nurses to share daily observations, dietary questions, and photos.
- **Emergency Signal Dispatch**: Integrated urgent alert broadcaster with dual-tone Web Audio alarm synthesis.

---

<!-- STREAMING_CHUNK:Detailing technical stack and system architecture -->
## 🛠️ Architecture & Technical Stack

| Layer | Technology | Details |
| :--- | :--- | :--- |
| **Frontend Framework** | HTML5 / Semantic DOM | Zero-dependency single-file deployment |
| **Styling & Theme** | Tailwind CSS CDN | Dark-slate clinical aesthetic (`nightSlate-950` / Teal accents) |
| **Visual Telemetry** | HTML5 2D Canvas API | High-DPI responsive time-series vital charting |
| **Hardware APIs** | MediaDevices (`getUserMedia`) | Front-facing camera access with mirror transformation |
| **Speech Recognition** | Web Speech API | Hands-free audio dictation for doctor consultations |
| **Sound Engine** | Web Audio API (`AudioContext`) | Synthesizes affirmative chimes & emergency alarms without MP3s |
| **Artificial Intelligence** | Google Gemini API (`gemini-3-flash`) | Structured JSON extraction for SOAP notes & clinical summaries |
| **Typography & Icons** | Inter, JetBrains Mono, FontAwesome 6.5 | Medical data clarity and high-contrast readability |

---

<!-- STREAMING_CHUNK:Providing quick start and setup instructions -->
## 🚀 Quick Start & Installation

Because CareSync is consolidated into a single self-contained file (`caresync_app.html`), no build tooling, Node.js packages, or compilation steps are required.

### Method 1: Direct File Launch
1. Download `caresync_app.html`.
2. Double-click the file to open it in any modern browser (Chrome, Edge, Safari, Firefox).
3. Allow camera and microphone permissions when prompted for the 2FA Check-In and NLP Scribe features.

### Method 2: Local HTTP Server (Recommended)
Running via a local HTTP server ensures smooth handling of media stream permissions across browsers:

```bash
# Using Python 3
python -m http.server 8080

# Using npx serve (Node.js)
npx serve .
```

Open your browser and navigate to:
```text
http://localhost:8080/caresync_app.html
```

---

<!-- STREAMING_CHUNK:Outlining API key configuration and security practices -->
## 🔑 Configuring the Gemini API Key

CareSync includes intelligent offline heuristic fallbacks for all NLP and AI briefings. To connect live, high-precision clinical reasoning:

1. Open `caresync_app.html` in your text editor.
2. Locate the `apiKey` variable in the `processClinicalNlpNotes()` and `generateAiHealthBriefing()` functions:
   ```javascript
   const apiKey = "YOUR_GEMINI_API_KEY_HERE";
   ```
3. Generate a free API key from [Google AI Studio](https://aistudio.google.com/).
4. Paste your key into both variables, save the file, and refresh your browser.

> **Security Note:** In production enterprise environments, API requests should be proxied through a HIPAA-compliant backend service with authenticated session tokens rather than calling directly from client-side scripts.

---

<!-- STREAMING_CHUNK:Documenting typical user journey and anti-isolation protocols -->
## 📋 User Workflow: A Typical Care Day

```text
  [Caregiver Arrives] ──> [Selfie 2FA Verification] ──> [Family Ledger Updates]
                                    │
                                    ▼
  [Doctor Visit] ────────> [Voice NLP Scribe] ────────> [SOAP & Rx Extracted]
                                    │
                                    ▼
  [Biometrics Logged] ────> [Canvas Radar Chart] ────> [AI Health Synthesis]
                                    │
                                    ▼
  [Milestones Met] ───────> [ADL Checklists Done] ───> [Peace of Mind Achieved]
```

1. **Shift Arrival**: Caregiver taps **"Selfie 2FA Check-In"**, activates their camera, selects "Shift Arrival & Baseline Vitals", and authenticates. Family members immediately see the verified arrival in the Ledger.
2. **Consultation Scribing**: When the visiting doctor conducts a review, the caregiver opens the **NLP Scribe**, presses **Record Audio**, and records the advice. Clicking **Synthesize** extracts structured SOAP records and medication changes.
3. **Trend Observation**: Family members open the **AI Vitals Analysis** tab to review 7-day BP stabilization trends and click **Synthesize Medical Brief** for a two-sentence clinical briefing.

---

<!-- STREAMING_CHUNK:Finalizing licensing and contribution notices -->
## 🔒 Privacy & Safety Notice

- **Camera Data**: Snapshot frames captured during 2FA checks remain local to the application state and are never transmitted to third-party tracking services.
- **Audio Dictation**: Voice streams captured through the Web Speech API are utilized strictly for consultation transcribing.
- **Clinical Disclaimer**: CareSync is an educational and assistive prototype designed to streamline coordination and is not a substitute for certified medical diagnosis or emergency 911 dispatch.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE). You are welcome to adapt, modify, and expand this platform for family caregiving, residential care facilities, or telehealth initiatives.
