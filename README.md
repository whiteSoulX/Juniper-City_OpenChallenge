# 🎯 JNPR Challenge System

[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen)](https://whitesoulx.github.io/Jnpr/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-active-success.svg)]()

> **Anonymous Challenge Platform for University Team Recruitment**  
> A gamified recruitment system designed to identify talented students passionate about networking, cybersecurity, and blockchain technology.

---

## 🚀 Live Demo

**Challenge URL:** ((https://whitesoulx.github.io/Juniper-City_OpenChallenge/))

**Owner Dashboard:** Add `?owner=JNPR2024` to URL for admin access

---

## 📋 Table of Contents

- [About](#about)
- [Features](#features)
- [Challenge Levels](#challenge-levels)
- [Tech Stack](#tech-stack)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Data Collection](#data-collection)
- [Security](#security)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## 📖 About

JNPR Challenge System is an interactive web-based recruitment platform designed for university capstone project team formation. The system evaluates students' technical skills through three progressive challenges while maintaining anonymity and collecting essential contact information.

### 🎯 Project Goals

- Identify students with genuine interest in networking, cybersecurity, and blockchain
- Create an engaging and fair evaluation process
- Maintain privacy through anonymous leaderboards
- Collect verified contact information for team formation
- Prevent answer sharing through AI-resistant interactive challenges

---

## ✨ Features

### 🔐 Anonymous Challenge System
- **Three Progressive Levels:** Network Analysis → Cryptography → Blockchain
- **Interactive Gameplay:** Visual puzzles, cipher wheels, blockchain simulation
- **AI-Resistant Design:** Requires human interaction, not just text-based answers
- **Real-time Validation:** Instant feedback on submissions

### 👥 Team Recruitment Portal
- **Anonymous Leaderboard:** Display top performers by codename and completion time
- **Verified Registration:** Collect university email, student ID, and phone numbers
- **Privacy Protection:** Contact details hidden from public (visible to validated users only)
- **Share Functionality:** Students can share challenge with peers

### 📊 Backend Integration
- **Google Sheets Database:** Automatic data collection to cloud spreadsheet
- **Three Data Streams:**
  - Leaderboard completions
  - Team registrations
  - Challenge attempts (success/failure tracking)
- **Owner Dashboard:** Admin panel with export and analytics features

### 🛡️ Security Features
- **Anti-cheat Protection:** Disabled console, right-click, and common dev shortcuts
- **Input Validation:** Email and phone number format verification
- **Session Tracking:** Unique session IDs for attempt monitoring
- **Offline Support:** Data queued locally and synced when online

---

## 🎮 Challenge Levels

### Level 1: 📡 Network Packet Analysis
**Concept:** Hex dump interpretation and ASCII decoding  
**Skills Tested:** Protocol understanding, hex-to-ASCII conversion  
**Difficulty:** ⭐⭐☆☆☆  
**Answer:** First letter from X-Secret header

```
0050: 58 2D 53 65 63 72 65 74 3A 20 4E 65 74 77 6F 72
      X  -  S  e  c  r  e  t  :     N  e  t  w  o  r
```

### Level 2: 🎡 Cipher Wheel Challenge
**Concept:** ROT13 Caesar cipher decryption  
**Skills Tested:** Cryptographic thinking, pattern recognition  
**Difficulty:** ⭐⭐⭐☆☆  
**Answer:** First letter of decoded word

```
Encrypted: FUBHEVGL
Decoded:   SECURITY (ROT13)
```

### Level 3: ⛓️ Blockchain Mining Simulator
**Concept:** Interactive blockchain mining  
**Skills Tested:** Understanding of distributed systems, hashing concepts  
**Difficulty:** ⭐⭐⭐⭐☆  
**Answer:** Letter revealed by completing all blocks

**Final Secret Key:** Combines all three answers (e.g., `NSBJNPR`)

---

## 🛠️ Tech Stack

### Frontend
- **HTML5** - Structure and semantic markup
- **CSS3** - Responsive design with modern animations
- **Vanilla JavaScript** - No frameworks, pure performance

### Backend
- **Google Apps Script** - Serverless backend API
- **Google Sheets** - Cloud database for data persistence

### Deployment
- **GitHub Pages** - Static site hosting (free)
- **GitHub Actions** - Optional CI/CD for automated deployments

### Key Technologies
- `Fetch API` - Asynchronous data transmission
- `LocalStorage API` - Offline data caching
- `CSS Grid & Flexbox` - Responsive layout system
- `Web Animations API` - Smooth interactive effects

---

## 📥 Installation

### Prerequisites
- GitHub account
- Google account (for backend)
- Text editor (VS Code recommended)

### Quick Start

1. **Clone the Repository**
```bash
git clone https://github.com/whiteSoulX/Jnpr.git
cd Jnpr
```

2. **Set Up Google Sheets Backend**
   - Create a new Google Sheet
   - Go to Extensions → Apps Script
   - Paste the backend code (see [Backend Setup](#backend-setup))
   - Deploy as Web App
   - Copy the deployment URL

3. **Configure HTML File**
   - Open `index.html`
   - Find line: `const BACKEND_URL = '...'`
   - Replace with your Apps Script URL

4. **Deploy to GitHub Pages**
   - Push to GitHub repository
   - Settings → Pages → Source: main branch
   - Save and wait 2-3 minutes

5. **Access Your Site**
   - Visit: `https://yourusername.github.io/Jnpr/`

---

## ⚙️ Configuration

### Backend Setup

1. **Create Google Sheet**
   - Name it: "JNPR Challenge Data"

2. **Add Apps Script Code**

```javascript
function doPost(e) {
  try {
    const sheet = SpreadsheetApp.getActiveSpreadsheet();
    const data = JSON.parse(e.postData.contents);
    
    let targetSheet;
    
    if (data.action === 'leaderboard') {
      targetSheet = sheet.getSheetByName('Leaderboard');
      if (!targetSheet) {
        targetSheet = sheet.insertSheet('Leaderboard');
        targetSheet.appendRow(['Timestamp', 'Nickname', 'Time', 'Final Key', 'User Info']);
      }
      targetSheet.appendRow([
        new Date().toISOString(),
        data.nickname,
        data.time,
        data.key,
        data.userInfo || 'Unknown'
      ]);
    } 
    else if (data.action === 'registration') {
      targetSheet = sheet.getSheetByName('Registrations');
      if (!targetSheet) {
        targetSheet = sheet.insertSheet('Registrations');
        targetSheet.appendRow(['Timestamp', 'Name', 'Email', 'Student ID', 'Phone', 'Additional', 'Key', 'Valid Key', 'User Info']);
      }
      targetSheet.appendRow([
        new Date().toISOString(),
        data.name,
        data.email,
        data.studentId,
        data.phone,
        data.additional,
        data.key,
        data.isValidKey ? 'YES' : 'NO',
        data.userInfo || 'Unknown'
      ]);
    }
    else if (data.action === 'attempt') {
      targetSheet = sheet.getSheetByName('Attempts');
      if (!targetSheet) {
        targetSheet = sheet.insertSheet('Attempts');
        targetSheet.appendRow(['Timestamp', 'Level', 'Answer', 'Correct', 'Session ID', 'User Info']);
      }
      targetSheet.appendRow([
        new Date().toISOString(),
        data.level,
        data.answer,
        data.correct ? 'YES' : 'NO',
        data.sessionId,
        data.userInfo || 'Unknown'
      ]);
    }
    
    return ContentService.createTextOutput(JSON.stringify({
      status: 'success'
    })).setMimeType(ContentService.MimeType.JSON);
    
  } catch (error) {
    return ContentService.createTextOutput(JSON.stringify({
      status: 'error',
      message: error.toString()
    })).setMimeType(ContentService.MimeType.JSON);
  }
}
```

3. **Deploy Settings**
   - Click: Deploy → New Deployment
   - Type: Web App
   - Execute as: **Me**
   - Who has access: **Anyone**
   - Deploy and copy URL

### Customization Options

**Change Owner Password:**
```javascript
// In HTML, find this line:
if (urlParams.get('owner') === 'JNPR2024') {
// Replace 'JNPR2024' with your secret
```

**Modify Valid Keys:**
```javascript
// In submitRegistration() function:
const validKeys = ['NSBJNPR']; // Add more keys here
```

**Update Announcement:**
```html
<!-- Find the announcement-banner div -->
<div class="announcement-banner">
    📡 Your custom announcement text here! 🚀
</div>
```

---

## 📱 Usage

### For Students

1. **Access Challenge**
   - Scan QR code or visit URL
   - Click "Start Challenge"

2. **Complete Levels**
   - Solve each level sequentially
   - Submit answers when confident
   - Use navigation arrows to preview next levels

3. **Choose Codename**
   - Enter 4-character anonymous nickname
   - View position on leaderboard

4. **Register for Team**
   - Fill required fields (Name, Email, ID, Phone)
   - Enter secret key (if completed)
   - Submit registration

### For Administrators

1. **Monitor Submissions**
   - Check Google Sheet for real-time data
   - Filter by "Valid Key" column for completions

2. **Access Owner Dashboard**
   - Visit: `yoursite.com/?owner=JNPR2024`
   - View full contact details
   - Export data as JSON

3. **Contact Students**
   - Use email list from Registrations sheet
   - Call/WhatsApp from phone numbers
   - Filter by completion status

---

## 📊 Data Collection

### Data Sheets Structure

**Sheet 1: Leaderboard**
```
Timestamp | Nickname | Time  | Final Key | User Info
----------|----------|-------|-----------|----------
ISO Date  | ZTEx     | 12:34 | NSBJNPR   | {...}
```

**Sheet 2: Registrations**
```
Timestamp | Name      | Email            | Student ID | Phone       | Additional | Key     | Valid | User Info
----------|-----------|------------------|------------|-------------|------------|---------|-------|----------
ISO Date  | John Doe  | john@uni.edu     | 2021-123   | +880 1234   | WhatsApp   | NSBJNPR | YES   | {...}
```

**Sheet 3: Attempts**
```
Timestamp | Level | Answer | Correct | Session ID  | User Info
----------|-------|--------|---------|-------------|----------
ISO Date  | 1     | N      | YES     | session_abc | {...}
```

### Privacy & Compliance

- **Anonymous Analytics:** Timezone, screen size, language (no IP addresses)
- **Contact Privacy:** Hidden from public unless challenge completed
- **Owner Access Only:** Full contact visibility restricted to admin mode
- **Data Export:** JSON backup available for GDPR compliance

---

## 🔒 Security

### Protection Measures

1. **Anti-Cheat:**
   - Console cleared every 2 seconds
   - Right-click disabled
   - F12, Ctrl+U, Ctrl+S blocked
   - Source code obfuscation

2. **Input Validation:**
   - Email format verification (regex)
   - Phone number validation (10+ digits)
   - Student ID required field
   - XSS protection (no eval, no innerHTML with user input)

3. **Rate Limiting:**
   - Session-based tracking
   - Offline data queue (prevents spam)
   - Duplicate nickname prevention

4. **Backend Security:**
   - CORS mode: no-cors (prevents token exposure)
   - Server-side validation in Apps Script
   - Timestamp verification for data integrity

### Responsible Disclosure

Found a security issue? Please email: [your-email@example.com]

Do NOT:
- ❌ Share exploits publicly
- ❌ Attack the production system
- ❌ Access other users' data

---

## 📸 Screenshots

### Homepage Dashboard
![Dashboard](https://via.placeholder.com/800x400?text=Dashboard+Screenshot)
*Leaderboard and registration portal*

### Challenge Interface
![Challenge](https://via.placeholder.com/800x400?text=Challenge+Screenshot)
*Network packet analysis level*

### Owner Dashboard
![Admin](https://via.placeholder.com/800x400?text=Admin+Panel+Screenshot)
*Full contact details with admin panel*

---

## 🤝 Contributing

Contributions are welcome! Please follow these guidelines:

### How to Contribute

1. **Fork the Repository**
```bash
git clone https://github.com/yourusername/Jnpr.git
```

2. **Create Feature Branch**
```bash
git checkout -b feature/AmazingFeature
```

3. **Commit Changes**
```bash
git commit -m 'Add some AmazingFeature'
```

4. **Push to Branch**
```bash
git push origin feature/AmazingFeature
```

5. **Open Pull Request**

### Contribution Ideas

- 🎨 UI/UX improvements
- 🧩 New challenge levels
- 🌐 Internationalization (i18n)
- 📱 Mobile app version
- 🔧 Backend alternatives (Firebase, Supabase)
- 📊 Analytics dashboard
- 🎓 Educational mode with hints

### Code Style

- Use ES6+ JavaScript features
- Follow semantic HTML5 principles
- CSS: BEM naming convention
- Comment complex logic
- Test on multiple browsers

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2024 JNPR Challenge Team

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## 📞 Contact

**Project Maintainer:** JNPR Team  
**Email:** [your-email@university.edu]  
**Website:** [https://whitesoulx.github.io/Jnpr/](https://whitesoulx.github.io/Jnpr/)  
**GitHub:** [@whiteSoulX](https://github.com/whiteSoulX)

### Project Links

- 🌐 **Live Demo:** [https://whitesoulx.github.io/Jnpr/](https://whitesoulx.github.io/Jnpr/)
- 📝 **Documentation:** [GitHub Wiki](https://github.com/whiteSoulX/Jnpr/wiki)
- 🐛 **Bug Reports:** [Issue Tracker](https://github.com/whiteSoulX/Jnpr/issues)
- 💡 **Feature Requests:** [Discussions](https://github.com/whiteSoulX/Jnpr/discussions)

---

## 🙏 Acknowledgments

- Inspired by CTF (Capture The Flag) competitions
- Built for university capstone project recruitment
- Special thanks to students who tested the challenge
- Open source community for tools and resources

---

## 📈 Project Stats

![GitHub stars](https://img.shields.io/github/stars/whiteSoulX/Jnpr?style=social)
![GitHub forks](https://img.shields.io/github/forks/whiteSoulX/Jnpr?style=social)
![GitHub issues](https://img.shields.io/github/issues/whiteSoulX/Jnpr)
![GitHub pull requests](https://img.shields.io/github/issues-pr/whiteSoulX/Jnpr)

---

## 🗺️ Roadmap

- [x] Basic challenge system
- [x] Google Sheets integration
- [x] Anonymous leaderboard
- [x] Contact collection
- [ ] Multi-language support
- [ ] Dark/Light theme toggle
- [ ] Advanced analytics dashboard
- [ ] Mobile app (React Native)
- [ ] Real-time multiplayer mode
- [ ] Certificate generation for completions

---

<div align="center">

**⭐ Star this repository if you find it helpful!**

Made with ❤️ by [JNPR Team](https://github.com/whiteSoulX)

[Report Bug](https://github.com/whiteSoulX/Jnpr/issues) · [Request Feature](https://github.com/whiteSoulX/Jnpr/issues) · [Documentation](https://github.com/whiteSoulX/Jnpr/wiki)

</div>
