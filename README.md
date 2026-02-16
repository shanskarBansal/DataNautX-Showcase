<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Django-5.2-092E20?style=for-the-badge&logo=django&logoColor=white" />
  <img src="https://img.shields.io/badge/Celery-5.x-37814A?style=for-the-badge&logo=celery&logoColor=white" />
  <img src="https://img.shields.io/badge/BigQuery-GCP-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white" />
  <img src="https://img.shields.io/badge/Redis-Queue-DC382D?style=for-the-badge&logo=redis&logoColor=white" />
  <img src="https://img.shields.io/badge/Gemini_2.5-AI-8E75B2?style=for-the-badge&logo=google&logoColor=white" />
  <img src="https://img.shields.io/badge/Railway-Deployed-0B0D0E?style=for-the-badge&logo=railway&logoColor=white" />
  <img src="https://img.shields.io/badge/Source-Private-red?style=for-the-badge&logo=github&logoColor=white" />
</p>

<h1 align="center">🚀 DataNautX</h1>

<p align="center">
  <strong>Enterprise-grade Social Media Intelligence Platform</strong><br/>
  Extract · Analyze · Report — across Facebook, Instagram, YouTube & X (Twitter)
</p>

<p align="center">
  <a href="#-screenshots">Screenshots</a> •
  <a href="#-key-features">Features</a> •
  <a href="#-architecture">Architecture</a> •
  <a href="#-tech-stack">Tech Stack</a> •
  <a href="#-license">License</a>
</p>

---

> ⚠️ **Note:** This is the **public showcase** repository. The source code is maintained in a private repository. For access or collaboration inquiries, please reach out via [GitHub](https://github.com/shanskarBansal).

---

## 📌 Overview

**DataNautX** is a full-stack data extraction & analytics platform that empowers non-technical users to collect, analyze, and generate reports from major social media platforms—all from a beautiful, modern web dashboard. Built with Django, backed by BigQuery, and deployed on Railway, it combines the power of LLM-driven insights with robust data engineering.

> **Built by** [Varahe Analytics](https://varahe.in) — communications engineering meets data science.

---

## 📸 Screenshots

### 🏠 Dashboard Home
> Project management with real-time activity feed, extraction stats, AI queries count, and quick actions

<p align="center">
  <img src="screenshots/01_dashboard_home.png" alt="Dashboard Home" width="100%" style="border-radius: 12px; box-shadow: 0 20px 60px rgba(0,0,0,0.3);" />
</p>

### ⚡ Extraction Workspace — Profile Data & Post Link Extraction
> Dual-mode extraction: **Profile Data Extraction** (Google Sheet / Manual grid) and **Post Link Extraction** with Handsontable spreadsheet editor, platform toggles (FB, IG, YT, X), date range selection, and real-time progress logs

<p align="center">
  <img src="screenshots/02_extraction_workspace.png" alt="Extraction Workspace" width="100%" style="border-radius: 12px; box-shadow: 0 20px 60px rgba(0,0,0,0.3);" />
</p>

### 🔍 Keyword Extraction
> Hashtag-based extraction across all platforms — choose Google Sheet or manual hashtag entry, set per-platform post limits (10/25/50/100), configure date ranges, and enable LLM analysis in one click. Re-run analysis on previous extractions without re-extracting data.

<p align="center">
  <img src="screenshots/03_keyword_extraction.png" alt="Keyword Extraction" width="100%" style="border-radius: 12px; box-shadow: 0 20px 60px rgba(0,0,0,0.3);" />
</p>

### 📊 Keyword Analysis Report
> Deep-dive analytics with sentiment analysis, narrative framing, rhetorical device detection, daily trends, top profiles, and top posts — all generated via Gemini 2.5 Flash LLM + statistical analysis pipeline. Exportable as interactive HTML report or PDF.

<p align="center">
  <img src="screenshots/04_keyword_analysis.png" alt="Keyword Analysis" width="100%" style="border-radius: 12px; box-shadow: 0 20px 60px rgba(0,0,0,0.3);" />
</p>

### 📈 Summary Studio
> Aggregate platform data for specific date ranges, generate summary tabs with engagement buckets (0k-1k through 100M+), and export directly to Google Sheets

<p align="center">
  <img src="screenshots/05_summary_studio.png" alt="Summary Studio" width="100%" style="border-radius: 12px; box-shadow: 0 20px 60px rgba(0,0,0,0.3);" />
</p>

### 📄 Report Generator
> Professional PDF reports with performance matrices, platform summaries, top posts with thumbnails, and executive notes — from CSV runs or Google Sheets data

<p align="center">
  <img src="screenshots/06_reporting.png" alt="Report Generator" width="100%" style="border-radius: 12px; box-shadow: 0 20px 60px rgba(0,0,0,0.3);" />
</p>

### 🤖 AI Assistant
> Natural language queries powered by Gemini 2.5 Flash — ask questions about your data in plain English, auto-generates BigQuery SQL, renders charts, and compares creators across platforms

<p align="center">
  <img src="screenshots/07_ai_assistant.png" alt="AI Assistant" width="100%" style="border-radius: 12px; box-shadow: 0 20px 60px rgba(0,0,0,0.3);" />
</p>

---

## ✨ Key Features

### 🔄 Profile Data Extraction
| Platform | Capabilities |
|----------|-------------|
| **Facebook** | Posts, reels, video content, engagement metrics, follower data |
| **Instagram** | Posts, reels, stories metrics, engagement & reach analytics |
| **YouTube** | Videos, shorts, channel stats, views/likes/comments/subscribers |
| **X (Twitter)** | Tweets, engagement, impressions, follower counts |

- Dual data sources: **Google Sheets** input or **manual spreadsheet entry** (Handsontable grid)
- Real-time progress monitoring with live extraction logs
- Concurrent multi-platform extraction via thread pools
- Automatic BigQuery synchronization & GCS file storage
- Reel/video-specific enrichment pipeline (FB Reels, IG Reels)

### 🔗 Post Link Extraction *(NEW)*
- **Direct URL enrichment** — paste any post link (FB, IG, YT, X) to extract full metrics
- Auto-detects platform from URL pattern
- Enriches with: Likes, Shares, Comments, Engagement, Total Reach, Post Date, Caption, Page Name, Followers
- Google Sheet or manual grid input with Handsontable editor
- Concurrent per-platform processing via ThreadPoolExecutor
- Output to Google Sheets + XLSX download

### 🔍 Keyword Extraction & Analysis *(NEW)*
- **Hashtag-based search** across Facebook, Instagram, YouTube & X simultaneously
- **Per-platform post limits** — configure 10, 25, 50, or 100 posts per platform per hashtag
- **Multi-hashtag support** — extract for multiple hashtags in parallel
- Google Sheet or manual hashtag grid input
- **LLM Analysis** (Gemini 2.5 Flash):
  - Sentiment classification (positive / negative / neutral) with confidence scores
  - Narrative framing detection (top 9 narrative frames + "Others")
  - Rhetorical device identification
  - Narrative strength scoring per topic
- **Data Analytics Pipeline**:
  - Topic overview (overall + per-platform)
  - Hashtag usage patterns (by platform & topic)
  - Risk factor indexing (topic × sentiment)
  - Sentiment distribution visualization
  - Daily engagement trends
  - Top profiles (overall + per-platform)
  - Top posts (by topic × sentiment × platform)
- **Re-run analysis** on previous extraction runs without re-extracting data
- **XLSX export** — download complete analysis workbook with all analytics sheets
- **Interactive HTML report** — keyword analysis rendered as a full-page interactive report

### 🤖 AI-Powered Assistant (Gemini 2.5 Flash)
- **Natural language queries** — ask questions in plain English about your extracted data
- **Intelligent SQL generation** — auto-generates & executes BigQuery queries
- **Smart understanding** — handles 200+ keywords and phrases for comprehensive question recognition
- **Visual charts** — request bar, pie, or line charts on-the-fly
- **Cross-platform comparisons** — compare creators, channels, accounts across platforms

### 📈 Reporting Suite
- **Automated PDF generation** with performance matrices, top posts, and executive summaries
- **Google Sheets integration** — read input, write output, and generate reports directly
- **CSV-based reports** from extraction runs
- **Report history** — access all previously generated reports with clean filenames

### 📊 Summary Studio
- **Aggregated summaries** — platform-wise summary reports with engagement buckets
- **Date range filtering** — analyze data for specific time periods
- **View count bucketing** — 16 granular buckets from 0k-1k to 100M+
- **Google Sheets output** — export summaries directly

### 🎨 Modern Web Dashboard
- **Glassmorphic design** — beautiful, modern UI with glassmorphism effects and holo-cards
- **Dark theme** with gradient accents and radial glow effects
- **Responsive design** — works seamlessly on desktop & mobile
- **Smooth animations** — letter-drop effects, count-up animations, GSAP transitions, tilt effects
- **Handsontable grid** — spreadsheet-like manual data entry with context menus
- **Real-time updates** — live extraction progress & status monitoring

### 🏢 Enterprise Features
- **Multi-project workspace** — isolated data, reports, and AI context per project
- **Google OAuth** — secure login with domain-restricted access
- **Celery + Redis** — distributed task queue for background processing
- **Ticket management** — internal issue tracking and collaboration
- **Scheduled extractions** — cron-based automated data collection (via django-celery-beat)
- **Worker health monitoring** — real-time Celery worker status dashboard
- **Google Drive integration** — auto-create Drive sheets for extraction runs
- **Activity history** — full timeline of extractions, AI queries, and reports

---

## 🏗 Architecture

```mermaid
flowchart TB
    subgraph WEB["🌐 Web Layer"]
        DJ["Django Web App\n(Gunicorn)"]
    end

    subgraph QUEUE["⚡ Task Queue"]
        CW["Celery Workers"]
        CB["Celery Beat\n(Scheduler)"]
    end

    subgraph STORAGE["💾 Data Stores"]
        PG[(PostgreSQL)]
        RD[(Redis\nBroker)]
    end

    subgraph ENGINE["🔄 Core Extraction Engine"]
        PE["Profile Data\nExtraction\n(FB, IG, YT, X)"]
        PL["Post Link\nExtraction\n(URL → Metrics)"]
        KE["Keyword\nExtraction\n(Hashtag)"]
        FB["Facebook"] & IG["Instagram"] & YT["YouTube"] & XX["X / Twitter"] & NA["News API"]
    end

    subgraph GCP["☁️ Google Cloud Platform"]
        BQ["BigQuery\n(DWH)"]
        GCS["GCS\n(Files)"]
        SM["Secret\nManager"]
        SH["Sheets\n(I/O)"]
    end

    subgraph AI["🤖 AI / Analytics Layer"]
        GM["Gemini 2.5\nFlash (LLM)"]
        SA["Sentiment\nAnalysis"]
        NF["Narrative\nFraming"]
        RH["Rhetorical\nDevices"]
        DT["Daily\nTrends"]
        TP["Top Profiles\n& Top Posts"]
    end

    DJ <--> CW <--> CB
    DJ --> PG
    CW --> RD
    CW --> PE & PL & KE
    PE & PL & KE --> FB & IG & YT & XX & NA
    FB & IG & YT & XX & NA --> BQ & GCS & SM & SH
    BQ --> GM & SA & NF & RH & DT & TP
```

---

## 🛠 Tech Stack

| Layer | Technologies |
|-------|-------------|
| **Frontend** | Django Templates, HTML5, CSS3 (Glassmorphism), JavaScript, GSAP, Three.js |
| **Backend** | Python 3.10+, Django 5.2, Gunicorn |
| **Spreadsheet UI** | Handsontable (Excel-like grid editor in browser) |
| **Task Queue** | Celery 5.x, Redis, django-celery-beat |
| **Database** | PostgreSQL (prod), SQLite (dev) |
| **Data Warehouse** | Google BigQuery |
| **Cloud Storage** | Google Cloud Storage (GCS) |
| **Secrets** | Google Secret Manager |
| **AI/ML** | Google Gemini 2.5 Flash, Pandas, NumPy |
| **PDF Generation** | Playwright (headless browser rendering) |
| **Scraping** | BrightData, Apify, Supermetrics, BeautifulSoup4 |
| **Deployment** | Railway (Procfile-based), Gunicorn |
| **Auth** | Google OAuth 2.0, Django Auth |

---

## 📊 BigQuery Schema

When BigQuery is enabled, extracted data is automatically pushed:

| Column | Type | Description |
|--------|------|-------------|
| `platform` | STRING | `fb`, `ig`, `yt`, or `x` |
| `run_timestamp` | STRING | Extraction timestamp (IST) |
| `post_id` | STRING | Unique post/video identifier |
| `post_url` | STRING | Direct link to the content |
| `created_datetime` | TIMESTAMP | Post creation time (UTC) |
| `content_type` | STRING | video, photo, reel, etc. |
| `caption_or_title` | STRING | Post caption or video title |
| `views` | INT64 | View count |
| `likes` | INT64 | Like/reaction count |
| `comments` | INT64 | Comment count |
| `shares` | INT64 | Share/retweet count |
| `followers` | INT64 | Follower count at extraction |
| `engagement` | INT64 | likes + comments + shares |
| `name` | STRING | Display name / Page name |
| `username` | STRING | Platform username/handle |
| `project_id` | STRING | Project identifier |

---

## 🔒 Security

- **Credentials** — All API keys & secrets stored in Google Secret Manager (never in code)
- **Authentication** — Google OAuth 2.0 with domain-restricted access
- **Environment** — Sensitive config via shell exports; `.gitignore` blocks all secret files
- **Database** — PostgreSQL with connection pooling in production
- **HTTPS** — SSL enforced in production deployments

---

> 🔒 **Source code is private.** For access, collaboration, or demo requests, please contact the maintainer via [GitHub](https://github.com/shanskarBansal).

---

## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

© 2025 Varahe Analytics Pvt Ltd

---

<p align="center">
  <sub>Built with ❤️ by <a href="https://varahe.in">Varahe Analytics</a> — Communications Engineering meets Data Science</sub>
</p>
