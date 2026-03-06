<div align="center">

<img src="https://img.shields.io/badge/version-7.0-00d4ff?style=flat-square&labelColor=04080f" />
<img src="https://img.shields.io/badge/license-MIT-00e87a?style=flat-square&labelColor=04080f" />
<img src="https://img.shields.io/badge/platform-Web%20%7C%20Mobile-a78bfa?style=flat-square&labelColor=04080f" />
<img src="https://img.shields.io/badge/AI-BlazePose%20%2B%20On--Device-f5c842?style=flat-square&labelColor=04080f" />
<img src="https://img.shields.io/badge/free-No%20signup%20required-00e87a?style=flat-square&labelColor=04080f" />

<br/><br/>

```
  ██████  ██████  ██ ███    ██ ███████ ███████ ██████  ███████  ██████ ████████  █████     █████  ██
  ██      ██   ██ ██ ████   ██ ██      ██      ██   ██ ██      ██         ██    ██   ██   ██   ██ ██
  ███████ ██████  ██ ██ ██  ██ █████   █████   ██████  █████   ██         ██    ███████   ███████ ██
       ██ ██      ██ ██  ██ ██ ██      ██      ██   ██ ██      ██         ██    ██   ██   ██   ██ ██
  ███████ ██      ██ ██   ████ ███████ ███████ ██   ██ ███████  ██████    ██    ██   ██   ██   ██ ██
```

**Clinical Posture Intelligence — Free, On-Device, No Signup**

*BlazePose · Real-time Skeleton Tracking · Personalised Health Alerts · Voice Coaching · Breath Analysis*

</div>

---

## 📸 Screenshots

<div align="center">
<table>
<tr>
<td align="center" width="33%">
<img src="assets/screen-wizard.svg" width="260" alt="Health Safety Wizard"/>
<br/><sub><b>4-Step Health Safety Wizard</b></sub>
<br/><sub>Cardiovascular, Spine & Breathing assessment</sub>
</td>
<td align="center" width="33%">
<img src="assets/screen-analysis.svg" width="260" alt="Live Posture Analysis"/>
<br/><sub><b>Live Posture Analysis</b></sub>
<br/><sub>33-landmark skeleton · Real-time metrics</sub>
</td>
<td align="center" width="33%">
<img src="assets/screen-alerts.svg" width="260" alt="Personalised Health Alerts"/>
<br/><sub><b>Smart Health Alerts</b></sub>
<br/><sub>Diabetes protocol · Breath coaching · BP cap</sub>
</td>
</tr>
</table>
</div>

---

## 🧠 What is SpineErectaAI?

**SpineErectaAI** is a fully client-side, AI-powered posture coach that runs entirely in your browser. It uses Google's **BlazePose** model to track 33 body landmarks at 30fps via your device camera — no video is ever uploaded, no account is required, and no data leaves your device.

It's built for **yoga practitioners, desk workers, physiotherapy patients, and athletes** who want real-time posture feedback personalised to their health profile.

> 🇮🇳 Built in India · Compliant with DPDPA 2023 · Tested on mobile & desktop

---

## ✨ Features

### 🦴 Spine & Posture Analysis
- Real-time **slouch angle detection** — calibrates to YOUR neutral spine on startup
- **Voice alert** fires after 3 seconds of continuous slouch
- Spine deviation shown as percentage from personalised neutral
- Visual skeleton overlay with glowing joint markers

### 🫁 Breath Intelligence
- **Clavicular vs Diaphragmatic** breathing detection via shoulder Y-axis movement
- Raised detection thresholds (CLV `0.018` / DPH `0.007`) — no false positives during belly breathing
- Alert fires only after **4 seconds of sustained** chest breathing
- Live breath waveform display
- HITL (Human-In-The-Loop) check-in when AI is uncertain

### 🤸 Inversion Pose Detection
- Detects Downward Dog, Forward Fold, Shoulder Stand and other inversions
- **Personalised hold-time cap** based on health conditions (8–60s)
- Counts down and warns before cap is reached
- Voice alert: "Please exit [pose] now"

### 🩺 Health Safety Profiles (12 Conditions)
| Condition | Cap | Risk Flags |
|-----------|-----|------------|
| High Blood Pressure | 10s | Inversion |
| Low Blood Pressure | 10s | Inversion |
| Cardiovascular Condition | 8s | Inversion |
| Diabetes (Type 1 or 2) | 15s | Reminder alerts |
| Disc Prolapse / Herniation | 8s | Inversion + Slouch |
| Spondylosis | 8s | Inversion + Slouch |
| Scoliosis | 10s | Inversion + Slouch |
| Lordosis | 10s | Inversion + Slouch |
| Recent Surgery (12 months) | 8s | Inversion + Slouch |
| Knee / Hip / Joint Issues | 15s | — |
| Asthma / Respiratory | 15s | Breath sensitivity |
| Anxiety / Panic Disorder | 15s | Calm voice pace |

### 🩺 Diabetes-Specific Alerts
- **On-session start**: Voice + visual advisory — blood sugar check, snack reminder, slow entry/exit guidance
- **Every 10 minutes**: Automated check-in during active session
- Covers: hypoglycemia prevention · dizziness warning · retinopathy precaution

### 🔊 Voice Coaching
- Web Speech API — no external TTS service
- Calm pace for anxiety conditions
- Personalised tips for each health flag
- Covers slouch correction, breath coaching, inversion warnings, diabetes check-ins

---

## 🚀 Getting Started

### Option 1 — Just open the file
```
No installation. No server. No npm.
```
1. Download `SpineErectaAI_v7.html`
2. Open it in Chrome, Edge, or Safari
3. Allow camera access when prompted
4. Complete the 4-step health profile
5. Click **▶ Start Analysis**

### Option 2 — Serve locally (recommended for mobile testing)
```bash
# Python
python3 -m http.server 8080

# Node
npx serve .

# Then open http://localhost:8080/SpineErectaAI_v7.html
```

### Option 3 — Deploy to GitHub Pages
```bash
git init
git add SpineErectaAI_v7.html
git commit -m "initial deploy"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/spineerectaai.git
git push -u origin main
# Enable Pages in repo Settings → Pages → Branch: main
```

---

## 🔧 Configuration

All settings are at the top of the file in the `CONFIG` object:

```javascript
const CONFIG = {
  FREE_MODE: true,           // No payments — unlimited access

  // Book a physio expert session
  CALENDLY_URL: 'https://calendly.com/YOUR_HANDLE/spine-consult',

  // Optional: sync anonymous usage to Google Sheets
  SHEETS_WEBHOOK: 'https://script.google.com/.../exec',

  // WhatsApp booking fallback
  SUPPORT_WA: '919876543210',   // country code + number, no +

  PRIVACY_URL: 'PrivacyPolicy_India.html',
};
```

---

## 🏗️ Architecture

```
SpineErectaAI_v7.html  (single-file app)
│
├── 🎨  CSS                   Dark UI design system
│       Design tokens, animations, responsive layout
│
├── 📋  Health Wizard          4-step gate (Location → Cardio → Spine → Breath)
│       12 condition Y/N cards, surgery detail, summary chips
│
├── 📹  Camera Pipeline
│       getUserMedia → BlazePose via MediaPipe CDN → Canvas overlay
│       Falls back to simulation mode if camera blocked
│
├── 🦴  processSpine()         Slouch angle from shoulder→hip midpoints
├── 🤸  processInv()           Inversion detection + timed cap
├── 🫁  processBreath()        Shoulder stdDev → clavicular classification
│       CLV=0.018, DPH=0.007, sustained 120-frame threshold
│
├── 🔊  speak()                Web Speech API voice coaching
├── 🔔  beep()                 Web Audio API tone alerts
│
└── 🩺  Health Alerts
        al-s  Slouch alert (red)
        al-b  Inversion limit alert (dark red)
        al-br Chest breathing alert (amber)
        al-d  Diabetes protocol alert (teal)
```

---

## 📱 Browser & Device Support

| Platform | Browser | Camera | Voice | Status |
|----------|---------|--------|-------|--------|
| Android | Chrome 90+ | ✅ | ✅ | ✅ Tested |
| iOS | Safari 15+ | ✅ | ✅ | ✅ Tested |
| Desktop | Chrome/Edge | ✅ | ✅ | ✅ Tested |
| Desktop | Firefox | ✅ | ✅ | ✅ Tested |
| Desktop | Safari | ✅ | ✅ | ✅ Tested |

> **Camera permission required.** If blocked, the app auto-starts a simulation demo with all alert systems active.

---

## 🔒 Privacy

- **Zero data upload** — all AI inference runs on-device via WebGL
- No cookies, no tracking, no analytics
- Health profile stored in memory only — cleared on page close
- No name, email or phone required
- Compliant with **India's DPDPA 2023**

---

## 📁 File Structure

```
spineerectaai/
├── SpineErectaAI_v7.html      # Main app (self-contained)
├── PrivacyPolicy_India.html   # Privacy policy (optional)
├── SpineErectaAI_Logo.svg     # Logo (optional, for Razorpay if re-enabled)
└── README.md
```

---

## 🛠️ Customisation

### Change slouch sensitivity
```javascript
// In processSpine() — default 30% from calibrated neutral
if(dev > 30) { /* slouch alert */ }
// Lower = more sensitive, Higher = more lenient
```

### Change breath detection thresholds
```javascript
const CLV = .018;  // Raise = less sensitive to chest breathing
const DPH = .007;  // Lower = more forgiving of slight shoulder movement
```

### Add a new health condition
```javascript
// In the CONDS array:
{
  id: 'myCondition',
  step: 4,                        // Which wizard step (3=cardio, 4=spine, 5=breath)
  q: 'My Condition Name',
  hint: 'Shown in wizard card',
  cap: 12,                        // Max inversion hold in seconds
  riskInv: true,                  // Restrict inversions?
  riskSlch: false                 // Stricter slouch monitoring?
}
```

---

## 🤝 Contributing

Pull requests welcome. Key areas for improvement:

- [ ] Improve breath detection with rib-cage landmark tracking
- [ ] Add rep counting for strength exercises
- [ ] Export session summary as PDF
- [ ] Add multi-language voice support
- [ ] Offline PWA manifest

---

## 📄 License

MIT License — free to use, modify and distribute.

---

## 👨‍⚕️ Disclaimer

SpineErectaAI is an assistive wellness tool, **not a medical device**. It does not diagnose or treat any medical condition. Always consult a qualified physiotherapist or physician before starting a new exercise programme, especially if you have the health conditions listed in this app.

---

<div align="center">
  <sub>Built with ❤️ · Powered by <a href="https://google.github.io/mediapipe/">MediaPipe BlazePose</a> · India DPDPA 2023 Compliant</sub>
</div>
