# 🎤 EchoCoach - Your Private AI Speaking Coach

**An offline Chrome Extension powered by Chrome's Built-in AI APIs**

## 📋 Overview

EchoCoach is a **100% offline, private AI-powered speaking coach** built with Chrome's Built-in AI APIs (Gemini Nano). It helps you practice speeches, presentations, and public speaking with real-time feedback—all without sending data to external servers.

### 🎯 Problem Solved

Many people struggle to:
- Practice speeches effectively in private
- Get instant, actionable feedback on their delivery
- Understand where they're losing confidence (fillers, pacing, etc.)
- Compare what they said with what they intended to say

**EchoCoach solves all of this** with AI-powered analysis, word-to-word script alignment checking, and personalized coaching tips.

---

## ✨ Features

✅ **Record your speech** - Up to 30 seconds of audio directly from the extension  
✅ **Script comparison** - Enter any script and get word-to-word alignment checking  
✅ **Accuracy scoring** - See how closely you followed the intended script  
✅ **AI-powered analysis** - Detects fillers, confidence level, speaking pace, and themes  
✅ **Delivery feedback** - Strengths + areas for improvement  
✅ **Polished rewrite** - Professional version of your speech  
✅ **Personalized tips** - 3 specific, actionable coaching suggestions  
✅ **100% offline** - All processing on your device using Gemini Nano  
✅ **Privacy-first** - No data collection, no cloud processing  
✅ **Beautiful UI** - Modern, accessible interface

---

## 🛠️ APIs Used (Chrome Built-in AI)

| API | Feature | Status |
|---|---|---|
| **Prompt API (LanguageModel)** | Core speech analysis | ✅ Working |
| **Proofreader API** | Grammar & style checking | ✅ Optional (requires token) |
| **Rewriter API** | Polished speech version | ✅ Optional (requires token) |
| **Writer API** | Personalized coaching tips | ✅ Optional (requires token) |

**Note:** The extension works perfectly with just the Prompt API. The optional APIs enhance functionality but require origin trial tokens.

---

## 📦 Installation & Setup

### **Prerequisites**

- Chrome 138+ (or Chromium-based browser)
- Windows 10+, macOS 13+, Linux, or ChromeOS
- 22+ GB free disk space (for Gemini Nano model download)
- 8GB+ RAM recommended

### **Step 1: Clone the Repository**

```bash
git clone https://github.com/Harsh134-R/EchoCoach.git
cd EchoCoach
```

### **Step 2: Enable Chrome Flags**

Open these URLs in Chrome and enable the following flags:

```
chrome://flags/#prompt-api-for-gemini-nano
chrome://flags/#prompt-api-for-gemini-nano-multimodal-input
chrome://flags/#optimization-guide-on-device-model
chrome://flags/#Proofreader-api-for-gemini-nano
chrome://flags/#Rewriter-api-for-gemini-nano
chrome://flags/#Writer-api-for-gemini-nano


```

**Steps:**
1. Paste URL in address bar
2. Click "Enabled" for each flag
3. Click "Relaunch Chrome" button
4. Chrome will restart and download the Gemini Nano model (~2GB)

### **Step 3: Load the Extension in Chrome**

1. Open `chrome://extensions/`
2. Enable **Developer mode** (toggle in top-right corner)
3. Click **Load unpacked**
4. Select the `EchoCoach` folder from your cloned repository
5. The extension icon should appear in your Chrome toolbar

### **Step 4 (Optional): Add Origin Trial Tokens for Enhanced APIs**

If you want **Proofreader, Rewriter, and Writer APIs** to work:

#### **4a. Get Your Extension ID**
1. Go to `chrome://extensions/`
2. Find "EchoCoach"
3. Copy the **ID** (looks like: `jnagjfbndfkneihjikgjfbhfdnkehig`)

#### **4b. Register for Origin Trials**
1. Go to https://developer.chrome.com/origintrials
2. Sign in with your Google account
3. Click **Register** for each API:
   - **Proofreader API**
   - **Writer API**
   - **Rewriter API** (may be grouped with Writer)
4. For each registration:
   - Enter: `chrome-extension://YOUR_EXTENSION_ID`
   - Accept terms
   - Copy the token provided

#### **4c. Add Tokens to Your Extension**

Open `popup.html` in the repository and find this section:

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>EchoCoach</title>
  
  <!-- 🔑 ADD THESE META TAGS WITH YOUR TOKENS -->
  <!-- Replace YOUR_PROOFREADER_TOKEN with actual token from origin trial -->
  <!-- Replace YOUR_WRITER_REWRITER_TOKEN with actual token from origin trial -->
  
  <link rel="stylesheet" href="styles.css">
</head>
```

**Add these meta tags** (replace with your actual tokens):

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>EchoCoach</title>
  
  <!-- 🔑 ORIGIN TRIAL TOKENS (uncomment and add your tokens) -->
  <!-- <meta http-equiv="origin-trial" content="YOUR_PROOFREADER_TOKEN_HERE"> -->
  <!-- <meta http-equiv="origin-trial" content="YOUR_WRITER_REWRITER_TOKEN_HERE"> -->
  
  <link rel="stylesheet" href="styles.css">
</head>
```

After pasting your tokens:

```html
  <meta http-equiv="origin-trial" content="Ar7k0jA5V4hN2pQ...">
  <meta http-equiv="origin-trial" content="Bq8m1kL9X2pR5sT...">
```

#### **4d. Reload the Extension**

1. Go to `chrome://extensions/`
2. Click **Reload** on EchoCoach
3. The optional APIs should now be active

---

## 🚀 How to Use

### **Basic Workflow**

1. **Open the extension** - Click EchoCoach icon in your Chrome toolbar
2. **(Optional) Enter a script** - Paste or type the speech you want to practice
3. **Click "Start Recording"** - You have 30 seconds to speak
4. **Wait for analysis** - AI analyzes your speech in real-time
5. **Review feedback:**
   - 📝 Speech Analysis (confidence, pace, fillers, topics)
   - 📋 Script Alignment (accuracy %, deviations, missing/extra words)
   - 💪 Delivery Assessment (strengths, improvements)
   - ✨ Polished Version (professional rewrite)
   - ⭐ AI Coach Tips (personalized advice)

### **Example Use Cases**

**Interview Prep:**
- Type common interview questions as scripts
- Practice answering and compare with ideal responses
- Get feedback on confidence and clarity

**Presentation Practice:**
- Paste your entire presentation as script
- Record yourself presenting a section
- Identify fillers and areas to improve

**Public Speaking:**
- Use famous speeches as scripts
- Record yourself reciting them
- Track improvement over time

---

## 📁 Project Structure

```
EchoCoach/
├── manifest.json          # Extension metadata
├── popup.html             # Extension UI
├── popup.js               # Main functionality & API integration
├── styles.css             # Styling
├── README.md              # This file
└── LICENSE                # MIT License
```

---

## 🔑 Important: Origin Trial Tokens

**Why tokens are removed from GitHub:**
- Security: Tokens are personal and shouldn't be in public repositories
- Abuse prevention: Others could use your tokens maliciously
- Best practice: Only store sensitive data locally

**For testing:**
- **Without tokens**: Full functionality with Prompt API analysis
- **With tokens**: Enhanced analysis with Grammar, Rewriting, and Tips APIs

---

## 🔧 Troubleshooting

### **Issue: "Chrome AI APIs not available"**
**Solution:**
- Ensure Chrome version is 138+
- Check all flags are enabled (chrome://flags/)
- Restart Chrome completely
- Reload extension (chrome://extensions/)

### **Issue: "Model downloading... Please wait"**
**Solution:**
- First use requires model download (~2GB)
- Wait for download to complete (can take 5-10 minutes)
- Check `chrome://on-device-internals` for download progress
- Ensure 22GB+ free disk space

### **Issue: Recording not working**
**Solution:**
- Grant microphone permission when prompted
- Check your system microphone works
- Try a different browser profile

### **Issue: "Proofreader/Writer/Rewriter unavailable"**
**Solution:**
- Add origin trial tokens to popup.html (see Step 4 above)
- Reload extension
- Tokens must match your extension ID exactly
- Wait for origin trial to activate (can take 1-2 hours)

---

## 📊 API Details

### **LanguageModel (Prompt API)**
- Analyzes speech for fillers, confidence, pace, themes
- Detects strengths and improvement areas
- Generates personalized coaching tips
- **Status:** Always available (core feature)

### **Proofreader API**
- Checks grammar and writing style
- Identifies corrections and suggestions
- **Status:** Optional (requires origin trial token)

### **Rewriter API**
- Creates professional version of your speech
- Enhances clarity and engagement
- **Status:** Optional (requires origin trial token)

### **Writer API**
- Generates personalized coaching tips
- Tailored to your specific performance
- **Status:** Optional (requires origin trial token)

---

## 💡 Key Features Explained

### **Script Alignment Checking**
- Compare what you said vs. what you planned
- Shows accuracy percentage (0-100%)
- Highlights specific deviations:
  - ❌ Substitutions (said different word)
  - ⚠️ Omissions (skipped words)
  - ➕ Additions (added extra words)

### **AI Analysis**
- **Fillers**: Detects "um", "uh", "like", "you know", etc.
- **Confidence**: 1-10 scale based on clarity and completeness
- **Pace**: Slow, moderate, or fast speaking speed
- **Themes**: Automatically extracts key topics discussed

### **Privacy & Security**
- ✅ 100% offline processing
- ✅ No cloud uploads
- ✅ No data collection
- ✅ Runs entirely on your device
- ✅ Gemini Nano is open source

---

## 📝 License

This project is licensed under the **MIT License** - see [LICENSE](LICENSE) file for details.

```
MIT License

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software...
```

---

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest features
- Submit pull requests

---

## 📞 Support & Feedback

- **Questions?** Check the [Troubleshooting](#-troubleshooting) section
- **Bug reports?** Open an issue on GitHub
- **Feature requests?** Let us know!

---

## 🎓 Built With

- **Chrome Built-in AI APIs** (Gemini Nano)
- **Web Audio API** (microphone recording)
- **Chrome Extension APIs**
- **HTML5, CSS3, JavaScript**

---

## 🚀 Roadmap

- [ ] Audio transcription using Web Speech API
- [ ] Session history & progress tracking
- [ ] Multiple language support
- [ ] Export feedback reports
- [ ] Integration with Google Docs for script input

---

## 📺 Demo Video

Watch the demo video here: [Insert YouTube/Vimeo link]

---

## 👨‍💻 Author

**Harsh** - Engineering Student
- GitHub: [@Harsh134-R](https://github.com/Harsh134-R)
- Built for: Google Chrome Built-in AI Challenge 2025

---

**Happy Speaking! 🎤✨**