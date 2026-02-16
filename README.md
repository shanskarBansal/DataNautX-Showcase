<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Django-5.2-092E20?style=for-the-badge&logo=django&logoColor=white" />
  <img src="https://img.shields.io/badge/Celery-5.x-37814A?style=for-the-badge&logo=celery&logoColor=white" />
  <img src="https://img.shields.io/badge/BigQuery-GCP-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white" />
  <img src="https://img.shields.io/badge/Redis-Queue-DC382D?style=for-the-badge&logo=redis&logoColor=white" />
  <img src="https://img.shields.io/badge/Railway-Deployed-0B0D0E?style=for-the-badge&logo=railway&logoColor=white" />
  <img src="https://img.shields.io/badge/Source-Private-red?style=for-the-badge&logo=github&logoColor=white" />
</p>

<h1 align="center">🚀 DataNautX</h1>

<p align="center">
  <strong>Enterprise-grade Social Media Intelligence Platform</strong><br/>
  Extract · Analyze · Report — across Facebook, Instagram, YouTube & X (Twitter)
</p>

<p align="center">
  <a href="#-key-features">Features</a> •
  <a href="#-architecture">Architecture</a> •
  <a href="#-tech-stack">Tech Stack</a> •
  <a href="#-getting-started">Getting Started</a> •
  <a href="#-deployment">Deployment</a> •
  <a href="#-license">License</a>
</p>

---

> ⚠️ **Note:** This is the **public showcase** repository. The source code is maintained in a private repository. For access or collaboration inquiries, please reach out directly.

---

## 📌 Overview

**DataNautX** is a full-stack data extraction & analytics platform that empowers non-technical users to collect, analyze, and generate reports from major social media platforms—all from a beautiful, modern web dashboard. Built with Django, backed by BigQuery, and deployed on Railway, it combines the power of LLM-driven insights with robust data engineering.

> **Built by** [Varahe Analytics](https://varahe.in) — communications engineering meets data science.

---

## ✨ Key Features

### 🔄 Multi-Platform Data Extraction
| Platform | Capabilities |
|----------|-------------|
| **Facebook** | Posts, reels, video content, engagement metrics, follower data |
| **Instagram** | Posts, reels, stories metrics, engagement & reach analytics |
| **YouTube** | Videos, shorts, channel stats, views/likes/comments/subscribers |
| **X (Twitter)** | Tweets, engagement, impressions, follower counts |

- Dual data sources: **Google Sheets** input or **manual data entry**
- Real-time progress monitoring with live extraction logs
- Concurrent multi-platform extraction via thread pools
- Automatic BigQuery synchronization & GCS file storage

### 🤖 AI-Powered Assistant (Gemini 2.5 Flash)
- **Natural language queries** — ask questions in plain English about your extracted data
- **Intelligent SQL generation** — auto-generates & executes BigQuery queries
- **Smart understanding** — handles 200+ keywords and phrases for comprehensive question recognition
- **Visual charts** — request bar, pie, or line charts on-the-fly
- **Cross-platform comparisons** — compare creators, channels, accounts across platforms

### 📊 Keyword & Narrative Analysis
- **Hashtag-based search** across all platforms simultaneously
- **Sentiment analysis** — positive, negative, neutral classification
- **Narrative framing** — rhetorical device detection & narrative strength scoring
- **Daily trend tracking** — engagement patterns over time
- **Top profiles & top posts** — identify key influencers and viral content
- **PDF export** — professional keyword analysis reports

### 📈 Reporting Suite
- **Automated PDF generation** with performance matrices, top posts, and executive summaries
- **Google Sheets integration** — read input, write output, and generate reports directly
- **CSV-based reports** from extraction runs
- **Report history** — access all previously generated reports with clean filenames

### 🎨 Modern Web Dashboard
- **Glassmorphic design** — beautiful, modern UI with glassmorphism effects
- **Dark theme** with gradient accents for comfortable extended use
- **Responsive design** — works seamlessly on desktop & mobile
- **Smooth animations** — letter-drop effects, counting animations, hover interactions
- **Real-time updates** — live extraction progress & status monitoring

### 🏢 Enterprise Features
- **Multi-project workspace** — isolated data, reports, and AI context per project
- **Google OAuth** — secure login with domain-restricted access
- **Celery + Redis** — distributed task queue for background processing
- **Ticket management** — internal issue tracking and collaboration
- **Scheduled extractions** — cron-based automated data collection
- **Worker health monitoring** — real-time Celery worker status dashboard

---

## 🏗 Architecture

```
┌───────────────────────────────────────────────────────────────────┐
│                        DataNautX Platform                        │
├───────────────────────────────────────────────────────────────────┤
│                                                                   │
│   ┌─────────────┐    ┌─────────────┐    ┌──────────────────┐     │
│   │   Django     │    │   Celery     │    │   Celery Beat    │     │
│   │   Web App    │◄──►│   Workers    │◄──►│   (Scheduler)    │     │
│   │   (Gunicorn) │    │             │    │                  │     │
│   └──────┬──────┘    └──────┬──────┘    └──────────────────┘     │
│          │                  │                                     │
│          ▼                  ▼                                     │
│   ┌─────────────┐    ┌─────────────┐                             │
│   │  PostgreSQL  │    │    Redis    │                             │
│   │  (Database)  │    │   (Broker)  │                             │
│   └─────────────┘    └─────────────┘                             │
│                                                                   │
│   ┌───────────────────────────────────────────────────────────┐  │
│   │              Core Extraction Engine                        │  │
│   │  ┌──────┐  ┌──────┐  ┌──────┐  ┌──────┐  ┌───────────┐  │  │
│   │  │  FB  │  │  IG  │  │  YT  │  │  X   │  │  News API │  │  │
│   │  └──┬───┘  └──┬───┘  └──┬───┘  └──┬───┘  └─────┬─────┘  │  │
│   │     └─────────┴────────┴─────────┴──────────────┘         │  │
│   └───────────────────────────┬───────────────────────────────┘  │
│                               │                                   │
│                               ▼                                   │
│   ┌───────────────────────────────────────────────────────────┐  │
│   │                   Google Cloud Platform                    │  │
│   │  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐ │  │
│   │  │ BigQuery  │  │   GCS    │  │  Secret  │  │  Sheets  │ │  │
│   │  │ (DWH)    │  │ (Files)  │  │  Manager │  │  (I/O)   │ │  │
│   │  └──────────┘  └──────────┘  └──────────┘  └──────────┘ │  │
│   └───────────────────────────────────────────────────────────┘  │
│                                                                   │
│   ┌───────────────────────────────────────────────────────────┐  │
│   │                    AI / Analytics Layer                    │  │
│   │  ┌──────────────┐  ┌──────────────┐  ┌────────────────┐  │  │
│   │  │ Gemini 2.5   │  │  Sentiment   │  │  Narrative     │  │  │
│   │  │ Flash (LLM)  │  │  Analysis    │  │  Framing       │  │  │
│   │  └──────────────┘  └──────────────┘  └────────────────┘  │  │
│   └───────────────────────────────────────────────────────────┘  │
└───────────────────────────────────────────────────────────────────┘
```

---

## 🛠 Tech Stack

| Layer | Technologies |
|-------|-------------|
| **Frontend** | Django Templates, HTML5, CSS3 (Glassmorphism), JavaScript |
| **Backend** | Python 3.10+, Django 5.2, Gunicorn |
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

## 📁 Project Structure

```
DataNautX/
├── main.py                     # Main extraction pipeline orchestrator
├── summary.py                  # Summary generation engine
├── requirements.txt            # Python dependencies
├── Procfile                    # Railway deployment configuration
├── LICENSE                     # MIT License
│
├── components/                 # Core extraction & integration modules
│   ├── fb_ig.py               # Facebook & Instagram extraction
│   ├── fb_reels.py            # Facebook Reels processing
│   ├── fb_video_reel.py       # Facebook Video/Reel data
│   ├── ig_reel.py             # Instagram Reels processing
│   ├── youtube.py             # YouTube extraction
│   ├── twitter.py             # X (Twitter) extraction
│   ├── news_fetcher.py        # News article fetcher
│   ├── bigquery_sink.py       # BigQuery data publisher
│   ├── google_api.py          # Google Sheets API integration
│   ├── project_store.py       # Project management & GCS storage
│   ├── secret_manager.py      # Google Secret Manager client
│   ├── redirect_url.py        # URL redirect resolver
│   ├── brightdata.py          # BrightData scraping integration
│   └── post_link_extraction/  # Post link extraction pipeline
│       ├── pipeline.py        # Extraction pipeline orchestrator
│       ├── processor.py       # Data processing logic
│       ├── utils.py           # Utility functions
│       └── sources/           # Platform-specific extractors
│           ├── fb.py, ig.py, x.py, yt.py
│
├── post-search/               # Keyword & narrative analysis module
│   ├── main.py                # Post search pipeline
│   ├── params.yaml            # Search configuration
│   └── src/
│       ├── data_analysis.py   # Statistical analysis
│       ├── llm_analysis.py    # LLM-powered insights
│       ├── scarpe_component.py# Scraping components
│       └── pipeline/          # Analysis pipeline
│           └── cal/           # Calculation modules
│               ├── sentiment_analysis.py
│               ├── narrative_frame.py
│               ├── narrative_strength.py
│               ├── daily_trends.py
│               ├── top_posts.py
│               ├── top_profiles.py
│               └── ...
│
├── webui/                     # Django web application
│   ├── manage.py              # Django management CLI
│   ├── webui/                 # Django project settings
│   │   ├── settings.py        # Application configuration
│   │   ├── celery.py          # Celery task queue config
│   │   ├── urls.py            # URL routing
│   │   └── wsgi.py / asgi.py  # WSGI/ASGI entry points
│   └── dashboard/             # Main dashboard app
│       ├── models.py          # Database models
│       ├── views.py           # View handlers (7,700+ lines)
│       ├── chatbot.py         # AI Assistant logic
│       ├── tasks.py           # Celery background tasks
│       ├── services.py        # Business logic services
│       ├── schedulers.py      # Scheduled extraction jobs
│       ├── forms.py           # Django forms
│       ├── urls.py            # App URL routing
│       ├── templates/         # 28 HTML templates
│       ├── management/        # Custom management commands
│       └── migrations/        # Database migrations
│
├── scripts/                   # Deployment & operational scripts
│   ├── release.sh             # Railway release (migrations)
│   ├── start_worker.sh        # Celery worker start
│   ├── start_beat.sh          # Celery beat scheduler start
│   ├── start_worker_local.sh  # Local development worker
│   └── start_beat_local.sh    # Local development beat
│
└── Link Extraction/           # Legacy link extraction module
    ├── main.py
    └── components/
```

---

## 🚀 Getting Started

### Prerequisites

- **Python 3.10+**
- **Google Cloud Platform** account with:
  - Secret Manager API enabled
  - BigQuery API (optional, for AI Assistant & data warehouse)
  - Cloud Storage API (optional, for file storage)
  - Service account JSON with appropriate permissions
- **Redis** (for Celery task queue)
- **PostgreSQL** (recommended for production; SQLite works for development)

> 🔒 **Source code is private.** For access, collaboration, or demo requests, please contact the maintainer via [GitHub](https://github.com/shanskarBansal).

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

## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

© 2025 Varahe Analytics Pvt Ltd

---

<p align="center">
  <sub>Built with ❤️ by <a href="https://varahe.in">Varahe Analytics</a> — Communications Engineering meets Data Science</sub>
</p>
