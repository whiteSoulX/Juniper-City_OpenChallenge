# 🎯 JNPR Challenge System

[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen)](https://whitesoulx.github.io/Jnpr/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-active-success.svg)]()

> **Anonymous Skills Assessment Platform for University Team Recruitment**

An interactive web-based challenge system designed to identify talented students passionate about networking, cybersecurity, and blockchain technology through gamified problem-solving.

---

## 🚀 Live Demo

**Challenge URL:** [https://whitesoulx.github.io/Juniper-City_OpenChallenge/] (https://whitesoulx.github.io/Juniper-City_OpenChallenge/)

---

## ✨ Features

- **🎮 3 Progressive Challenge Levels** - Network Analysis, Cryptography, Blockchain
- **🔐 Anonymous Leaderboard** - Compete with codenames, maintain privacy
- **📊 Automated Data Collection** - Google Sheets backend integration
- **👥 Team Registration Portal** - Collect verified university contact info
- **🛡️ AI-Resistant Design** - Interactive puzzles prevent answer sharing
- **📱 Fully Responsive** - Works on desktop, tablet, and mobile

---

## 🎮 Challenge Overview

### Level 1: Network Packet Analysis 📡
Analyze hex dumps and decode network protocols to extract hidden information.

**Skills Tested:** Protocol understanding, hex-to-ASCII conversion, packet inspection

### Level 2: Cipher Wheel Challenge 🎡
Decrypt encrypted messages using classical cryptography techniques.

**Skills Tested:** Cryptographic thinking, pattern recognition, cipher decryption

### Level 3: Blockchain Mining Simulator ⛓️
Complete a simulated blockchain by mining blocks and understanding distributed systems.

**Skills Tested:** Blockchain concepts, hash functions, distributed ledger technology

**Complete all levels to unlock your secret key and join the team! 🔑**

---

## 🛠️ Tech Stack

- **Frontend:** HTML5, CSS3, Vanilla JavaScript
- **Backend:** Google Apps Script
- **Database:** Google Sheets
- **Hosting:** GitHub Pages (Free)

---

## 📥 Quick Start

### 1. Clone Repository
```bash
git clone https://github.com/whiteSoulX/Jnpr.git
cd Jnpr
```

### 2. Setup Google Sheets Backend
- Create a new Google Sheet
- Add the Apps Script code (see `backend-setup.md`)
- Deploy as Web App
- Copy deployment URL

### 3. Configure
- Open `index.html`
- Update `BACKEND_URL` with your Apps Script URL
- Customize announcement text (optional)

### 4. Deploy
- Push to GitHub repository
- Enable GitHub Pages (Settings → Pages → Source: main branch)
- Access your site at `https://yourusername.github.io/Jnpr/`

---

## 📊 Data Collection

The system automatically collects data into 3 Google Sheets tabs:

1. **Leaderboard** - Anonymous completions with nicknames and times
2. **Registrations** - Full contact details (name, email, student ID, phone)
3. **Attempts** - All challenge attempts (right/wrong answers)

### Owner Access
Visit your site with `?owner=JNPR2024` parameter to see full contact details and admin panel.

---

## 🔒 Security & Privacy

- **Anonymous Leaderboard** - Public shows only codenames
- **Contact Privacy** - Details hidden unless challenge completed
- **Anti-Cheat Protection** - Console blocking, input validation
- **Session Tracking** - Unique IDs for attempt monitoring
- **Offline Support** - Data queued and synced when online

---

## 📱 Usage

### For Students
1. Access the challenge via URL or QR code
2. Solve 3 progressive levels
3. Choose a 4-character anonymous codename
4. Register with university details to join the team

### For Administrators
1. Monitor submissions in Google Sheet
2. Use owner mode (`?owner=JNPR2024`) to view full contacts
3. Export data and contact top performers
4. Form your team from validated completions

---

## 🎯 Use Cases

- **University Capstone Projects** - Recruit skilled team members
- **Hackathon Pre-screening** - Filter qualified participants
- **Student Clubs** - Evaluate technical knowledge for membership
- **Corporate Training** - Assess employee cybersecurity awareness
- **Educational Workshops** - Gamified learning assessment

---

## 🤝 Contributing

Contributions are welcome! Here's how:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

**Ideas for Contribution:**
- New challenge levels
- UI/UX improvements
- Multi-language support
- Mobile app version
- Advanced analytics dashboard

---

## 📄 License

This project is licensed under the MIT License - see [LICENSE](LICENSE) for details.

---

## 📞 Contact

**Project:** JNPR Challenge System  
**Website:** [https://whitesoulx.github.io/Jnpr/](https://whitesoulx.github.io/Jnpr/)  
**GitHub:** [@whiteSoulX](https://github.com/whiteSoulX)  
**Issues:** [Report Bug or Request Feature](https://github.com/whiteSoulX/Jnpr/issues)

---

## 🙏 Acknowledgments

- Inspired by CTF (Capture The Flag) competitions
- Built for university team recruitment
- Thanks to the open-source community

---

## 🗺️ Roadmap

- [x] Core challenge system
- [x] Google Sheets integration
- [x] Anonymous leaderboard
- [x] Contact collection system
- [ ] Multi-language support
- [ ] Certificate generation
- [ ] Advanced analytics
- [ ] Real-time multiplayer mode

---

<div align="center">

**⭐ Star this repository if you find it helpful!**

**Made with ❤️ for the tech community**

[Live Demo](https://whitesoulx.github.io/Jnpr/) • [Report Bug](https://github.com/whiteSoulX/Jnpr/issues) • [Request Feature](https://github.com/whiteSoulX/Jnpr/issues)

</div>
