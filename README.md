<div align="center"><img src="app/app/src/main/res/mipmap-xxxhdpi/ic_launcher.webp" width="120" alt="Flowy Logo"/>🌸 Flowy

A calmer, smarter way to understand your cycle.

<p>
  <img src="https://readme-typing-svg.demolab.com?font=Quicksand&weight=600&size=22&pause=1200&color=E85D9E&center=true&vCenter=true&width=650&lines=Your+cycle.+Your+body.+Your+rhythm.;Private+%E2%80%A2+Secure+%E2%80%A2+Personal;Cycle+tracking+with+a+human+touch.;Built+with+Kotlin+%2B+Jetpack+Compose+%F0%9F%8C%B8" alt="Typing animation"/>
</p><p>
  <a href="https://github.com/im-aswajith/FLOWY">
    <img src="https://img.shields.io/github/stars/im-aswajith/FLOWY?style=for-the-badge&logo=github&label=STARS" alt="GitHub Stars"/>
  </a>
  <a href="https://github.com/im-aswajith/FLOWY/issues">
    <img src="https://img.shields.io/github/issues/im-aswajith/FLOWY?style=for-the-badge&logo=github&label=ISSUES" alt="GitHub Issues"/>
  </a>
  <a href="https://github.com/im-aswajith/FLOWY">
    <img src="https://img.shields.io/github/repo-size/im-aswajith/FLOWY?style=for-the-badge&logo=github&label=SIZE" alt="Repository Size"/>
  </a>
  <img src="https://img.shields.io/badge/Kotlin-2.x-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white" alt="Kotlin"/>
  <img src="https://img.shields.io/badge/Jetpack%20Compose-UI-4285F4?style=for-the-badge&logo=jetpackcompose&logoColor=white" alt="Jetpack Compose"/>
</p><p>
  <strong>🌷 Track • Understand • Care • Protect</strong>
</p></div>---

🌸 What is Flowy?

Flowy is a modern Android cycle and menstrual-care companion designed to make period tracking feel less clinical and more human.

Instead of simply showing a calendar, Flowy combines:

«🩸 Cycle tracking
🌙 Phase awareness
💧 Hydration reminders
🧼 Hygiene care
🔐 Encrypted personal data
📚 Health education
💗 Daily motivational guidance»

The goal is simple:

Help people understand their body's rhythm — while keeping their personal data protected.

---

<div align="center">🌺 Four phases. One rhythm.

🩸 Menstrual → 🌱 Follicular → ✨ Ovulatory → 🌙 Luteal

</div>---

✨ Features

<table>
<tr>
<td width="50%">🩸 Smart Cycle Tracking

- Log period start dates
- Configurable cycle length
- Configurable period length
- Automatic cycle-day calculation
- Current phase detection
- Next-period forecasting
- Historical cycle logging
- Average cycle analysis

</td><td width="50%">🌙 Phase Awareness

Flowy understands the four major cycle phases:

- 🩸 Menstrual
- 🌱 Follicular
- ✨ Ovulatory
- 🌙 Luteal

Each phase provides contextual information, descriptions and motivational guidance.

</td>
</tr><tr>
<td>🧼 Hygiene Care Hub

During the active menstrual phase, Flowy can provide:

- Product selection
- Hygiene-change timer
- Remaining-time tracking
- Overdue detection
- Product-specific recommendations
- Automatic hygiene reminders

Supported products include:

"Pads" • "Panty Liners" • "Tampons" • "Cups/Discs" • "Period Underwear"

</td><td>💧 Smart Reminders

Flowy schedules useful notifications such as:

- Upcoming period
- One-day-before reminder
- Period-day reminder
- Hygiene/product-change reminders
- Hydration reminders

Notifications are scheduled using Android's alarm system.

</td>
</tr><tr>
<td>📚 Health Education

A dedicated education section provides:

- Cycle information
- Phase explanations
- Self-care guidance
- Health-literacy content
- Practical action tips
- Expandable educational topics

</td><td>🔐 Privacy First

Sensitive cycle information is encrypted before being stored.

Flowy's cryptographic layer uses:

- AES-256-GCM
- HKDF-SHA256
- 256-bit master key
- Random 12-byte nonces
- 128-bit authentication tag
- User-ID-bound AAD

</td>
</tr>
</table>---

🔐 Security Architecture

Flowy doesn't treat cycle information like ordinary application data.

The project implements a dedicated encryption layer around sensitive fields.

                    ┌─────────────────────┐
                    │     User Profile    │
                    │                     │
                    │  Cycle information  │
                    │  Product settings   │
                    │  Reminder settings  │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │    FieldCipher      │
                    └──────────┬──────────┘
                               │
                     HKDF-SHA256
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Per-user AES Key    │
                    └──────────┬──────────┘
                               │
                         AES-256-GCM
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Encrypted Database  │
                    │                     │
                    │ Room + Ciphertext   │
                    └─────────────────────┘

Cryptographic design

Layer| Implementation
Master key| 256-bit
Key derivation| HKDF-SHA256
Encryption| AES-256-GCM
Authentication tag| 128-bit
Nonce| 12-byte random nonce
AAD| User ID
Storage format| URL-safe Base64
Database| Room

The implementation derives a user-specific encryption key from the master key using HKDF-SHA256 and binds ciphertext authentication to the user ID through AAD.

«Note: Encryption improves protection of stored data, but it should not be interpreted as a guarantee of absolute security. Production deployments should additionally use Android Keystore-backed key protection, secure release signing, threat modeling and independent security review.»

---

🧠 Cycle Engine

Flowy's cycle calculation engine models the cycle as four phases.

                ┌────────────────┐
                │    MENSTRUAL   │
                │      🩸        │
                └───────┬────────┘
                        │
                        ▼
                ┌────────────────┐
                │   FOLLICULAR   │
                │      🌱        │
                └───────┬────────┘
                        │
                        ▼
                ┌────────────────┐
                │    OVULATORY   │
                │      ✨        │
                └───────┬────────┘
                        │
                        ▼
                ┌────────────────┐
                │     LUTEAL     │
                │      🌙        │
                └───────┬────────┘
                        │
                        └──────────────► 🩸

The cycle engine calculates:

- Current cycle day
- Current phase
- Next expected period
- Days remaining
- Historical average cycle length
- Cycle progress
- Phase-specific motivational messaging

---

🎨 UI & Experience

Flowy is built around a calm, soft and responsive interface.

Visual experience

- 🌈 Animated gradient background
- 🎡 Animated cycle wheel
- 💫 Animated screen transitions
- 🃏 Material 3 elevated cards
- 🌙 Theme support
- 📱 Edge-to-edge Android UI
- 🧭 Bottom navigation
- 🎯 Interactive cycle controls
- 🔄 Refreshable motivational messages

The UI is implemented using Jetpack Compose, allowing the interface to remain declarative and highly composable.

---

🏗️ Architecture

                         ┌─────────────────────┐
                         │     MainActivity    │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │    FlowyViewModel   │
                         └──────────┬──────────┘
                                    │
                    ┌───────────────┼───────────────┐
                    │               │               │
                    ▼               ▼               ▼
             ┌────────────┐  ┌─────────────┐  ┌──────────────┐
             │ UI Screens │  │ Cycle Model │  │   Services   │
             └─────┬──────┘  └─────────────┘  └──────┬───────┘
                   │                                  │
                   ▼                                  ▼
             ┌────────────┐                   ┌──────────────┐
             │ Components │                   │ AlarmManager │
             └─────┬──────┘                   │ Foreground   │
                   │                          │ Service      │
                   │                          └──────────────┘
                   ▼
             ┌──────────────────┐
             │ FlowyRepository  │
             └────────┬─────────┘
                      │
             ┌────────┴────────┐
             │                 │
             ▼                 ▼
      ┌─────────────┐   ┌──────────────┐
      │ Room DAO    │   │ FieldCipher  │
      └──────┬──────┘   └──────┬───────┘
             │                 │
             ▼                 ▼
      ┌─────────────┐   ┌────────────────┐
      │ Local DB    │   │ AES-256-GCM    │
      └─────────────┘   └────────────────┘

---

📂 Project Structure

FLOWY/
│
├── app/
│   ├── src/
│   │   ├── main/
│   │   │
│   │   ├── java/com/example/
│   │   │   │
│   │   │   ├── MainActivity.kt
│   │   │   │
│   │   │   ├── crypto/
│   │   │   │   └── FieldCipher.kt
│   │   │   │
│   │   │   ├── data/
│   │   │   │   ├── Daos.kt
│   │   │   │   ├── Entities.kt
│   │   │   │   ├── FlowyDatabase.kt
│   │   │   │   └── FlowyRepository.kt
│   │   │   │
│   │   │   ├── model/
│   │   │   │   ├── CycleCalculator.kt
│   │   │   │   └── Models.kt
│   │   │   │
│   │   │   ├── service/
│   │   │   │   ├── FlowyAlarmReceiver.kt
│   │   │   │   ├── FlowyAlertScheduler.kt
│   │   │   │   ├── FlowyForegroundService.kt
│   │   │   │   └── FlowyNotificationHelper.kt
│   │   │   │
│   │   │   └── ui/
│   │   │       ├── FlowyViewModel.kt
│   │   │       ├── components/
│   │   │       ├── screens/
│   │   │       ├── theme/
│   │   │       └── util/
│   │   │
│   │   └── res/
│   │
│   ├── build.gradle.kts
│   └── proguard-rules.pro
│
├── build.gradle.kts
├── gradle.properties
├── settings.gradle.kts
├── .env.example
└── README.md

---

🧩 Main Components

"CycleCalculator"

The core cycle intelligence layer.

Responsible for:

Period data
     ↓
Cycle calculation
     ↓
Current phase
     ↓
Cycle status
     ↓
Forecast + guidance

---

"FieldCipher"

The security layer responsible for encrypting and decrypting sensitive fields.

Master Key
    ↓
HKDF-SHA256
    ↓
User-specific key
    ↓
AES-256-GCM
    ↓
Ciphertext

---

"FlowyRepository"

Acts as the bridge between the application and persistent storage.

It handles:

- Profile persistence
- Period logs
- Encryption/decryption
- Product changes
- Cycle settings
- Database operations

---

"FlowyAlertScheduler"

Controls scheduled notifications.

Current reminder categories include:

🩸 Period reminders
🧼 Hygiene reminders
💧 Hydration reminders

---

🛠️ Tech Stack

<div align="center"><img src="https://skillicons.dev/icons?i=kotlin,androidstudio,gradle,firebase,git,github" alt="Tech Stack"/></div>Core

- Kotlin
- Android SDK
- Jetpack Compose
- Material 3
- AndroidX
- Room
- Kotlin Coroutines
- ViewModel
- KSP

Security

- AES-256-GCM
- HKDF-SHA256
- SecureRandom
- Authenticated encryption
- User-bound AAD

Android Services

- AlarmManager
- BroadcastReceiver
- Foreground Service
- Notifications

Testing

- JUnit
- Robolectric
- Compose UI testing
- Roborazzi screenshot testing

---

🚀 Getting Started

1️⃣ Clone the repository

git clone https://github.com/im-aswajith/FLOWY.git
cd FLOWY

2️⃣ Open in Android Studio

Open the cloned directory using:

Android Studio
      ↓
Open
      ↓
FLOWY/

3️⃣ Configure environment values

Copy:

.env.example

to:

.env

Then configure the required project-specific values.

4️⃣ Build the application

On Windows:

.\gradlew.bat assembleDebug

On macOS/Linux:

./gradlew assembleDebug

5️⃣ Run

Connect an Android device or launch an emulator and run the "app" configuration from Android Studio.

---

🧪 Testing

Flowy includes both unit and UI-oriented testing.

Example test areas include:

Cycle calculation
       │
       ├── Phase detection
       ├── Period forecasting
       ├── Cycle history
       │
       ▼
Encryption
       │
       ├── Encrypt/decrypt
       ├── Key handling
       └── Authentication
       │
       ▼
UI
       │
       ├── Compose tests
       └── Screenshot tests

Run tests with:

./gradlew test

Windows:

.\gradlew.bat test

---

🌱 Design Philosophy

Flowy isn't designed to make users obsess over numbers.

It's designed to encourage awareness.

Instead of:

«"Your cycle is just a date."»

Flowy aims for:

«"Your body is communicating with you."»

The application combines useful information with gentle messaging so the experience feels supportive rather than overwhelming.

---

🔒 Privacy Philosophy

Personal cycle information can be extremely sensitive.

Flowy's data layer therefore separates:

Application Logic
        │
        ▼
Repository
        │
        ▼
Encryption Layer
        │
        ▼
Local Persistence

Sensitive fields are encrypted before being written to the Room database.

The project also includes a settings/privacy area where database and cipher information can be inspected and user data can be erased.

---

🗺️ Roadmap

«The roadmap is intentionally open-ended as Flowy evolves.»

🌸 Core

- [x] Cycle tracking
- [x] Four-phase cycle model
- [x] Period history
- [x] Period forecasting
- [x] Motivational messages
- [x] Hygiene timer
- [x] Product selection
- [x] Hydration reminders
- [x] Period notifications

🔐 Privacy

- [x] Encrypted sensitive fields
- [x] AES-256-GCM
- [x] HKDF-SHA256
- [x] Master-key lifecycle
- [x] Delete-all-data flow

📚 Education

- [x] Health education section
- [x] Cycle phase explanations
- [x] Self-care guidance

🚀 Future possibilities

- [ ] More detailed analytics
- [ ] Backup/export system
- [ ] Wearable integration
- [ ] More accessibility improvements
- [ ] More personalization
- [ ] Advanced cycle insights
- [ ] Improved privacy architecture
- [ ] Production-grade Android Keystore integration

---

⚠️ Health Disclaimer

Flowy is intended as an educational and personal tracking tool.

Cycle predictions are estimates and should not be treated as medical diagnosis, contraception, fertility diagnosis, or emergency medical advice.

If you experience unusual, severe, persistent or concerning symptoms, consult a qualified healthcare professional.

---

🤝 Contributing

Contributions, ideas and improvements are welcome.

# Fork
# Create a branch
git checkout -b feature/amazing-feature

# Make your changes
git add .

# Commit
git commit -m "feat: add amazing feature"

# Push
git push origin feature/amazing-feature

Then open a Pull Request.

---

🐛 Issues & Ideas

Found a bug?

Have an idea?

Want to improve Flowy?

Open an issue:

<p align="center">
  <a href="https://github.com/im-aswajith/FLOWY/issues">
    <img src="https://img.shields.io/badge/Report%20an%20Issue-E85D9E?style=for-the-badge&logo=github&logoColor=white" alt="Report Issue"/>
  </a>
</p>---

⭐ Support Flowy

If you find this project interesting, consider giving it a ⭐ on GitHub.

It helps the project get more visibility and motivates future development.

<p align="center">
  <a href="https://github.com/im-aswajith/FLOWY">
    <img src="https://img.shields.io/github/stars/im-aswajith/FLOWY?style=social" alt="Star Flowy"/>
  </a>
</p>---

👨‍💻 Developer

<div align="center"><img src="https://github.com/im-aswajith.png" width="110" height="110" style="border-radius:50%;" alt="Aswajith"/>Aswajith

Building things with code, curiosity and a lot of experimentation. 🚀

<p>
  <a href="https://github.com/im-aswajith">
    <img src="https://img.shields.io/badge/GitHub-im--aswajith-181717?style=for-the-badge&logo=github" alt="GitHub"/>
  </a>
</p></div>---

📊 GitHub Activity

<div align="center"><img src="https://github-readme-stats.vercel.app/api?username=im-aswajith&show_icons=true&hide_border=true&rank_icon=github" height="165" alt="GitHub Stats"/><img src="https://github-readme-stats.vercel.app/api/top-langs/?username=im-aswajith&layout=compact&hide_border=true" height="165" alt="Top Languages"/></div>---

<div align="center">🌸 Made with Kotlin, curiosity & care.

Flowy — Your cycle. Your rhythm. Your space.

<br/><img src="https://capsule-render.vercel.app/api?type=waving&height=120&section=footer&color=gradient" alt="Footer"/></div>
