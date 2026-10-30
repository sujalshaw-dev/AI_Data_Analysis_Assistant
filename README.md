# 🚀 DataNova AI — Intelligent Conversational Data Analytics

**DataNova AI** is a modern, enterprise-grade, full-stack AI-powered data analytics web application. Users can upload CSV or Excel files, explore live schemas, ask questions in natural language, and instantly get accurate data insights, calculations, interactive visualizations, and downloadable executive PDF reports.

Designed with a premium dark UI featuring vibrant blue-purple gradients, glassmorphism panels, and fluid responsive transitions.

---

## ✨ Key Features

- **📂 Multi-Format Ingestion**: Upload `.csv`, `.xlsx`, or `.xls` files with automatic delimiter detection, UTF-8/Latin-1 encoding fallback, and multi-sheet parsing.
- **⚡ 1-Click Curated Sample Datasets**:
  - *Global E-Commerce Sales*: 600 orders with sales, profit, discounts, and regional segments.
  - *Tech Industry Financials*: Top tech leaders with market caps, revenue, profit margins, and R&D spend.
  - *Employee HR & Attrition*: 400 employee records with salaries, satisfaction ratings, and turnover.
- **💬 Conversational AI Analyst**:
  - Natural language querying powered by **Google Gemini 2.5 Flash** or **OpenAI GPT-4o**.
  - **Zero-Key Smart Analyst Engine**: High-performance rule-based & pandas parser that works **out-of-the-box with zero API key required**!
  - Responses include clear executive narrative, KPI highlight badges, dynamic Chart.js visualizations, executable Python/Pandas logic, and smart follow-up suggestions.
- **📊 Automated Exploratory Data Analysis (EDA)**:
  - Dataset health metrics (rows, columns, completeness %, duplicates, memory footprint).
  - Automated anomaly alerts, high correlation notifications, and dominant category flags.
  - Interactive searchable & sortable data table with custom filtering (`==`, `!=`, `>`, `<`, `contains`, null checks) and pagination.
  - **Column Profiler**: Click any column to view min/max/mean/median/std/quartiles, IQR outlier counts, and frequency distributions.
- **📈 Chart Studio & Visual Builder**:
  - Build custom Bar, Line, Area, Doughnut, Pie, and PolarArea charts.
  - Configure X-Axis, Y-Axis, Aggregations (Sum, Mean, Median, Min, Max, Count), and Group-By multi-series comparisons.
  - 1-click PNG export with custom dark-themed tooltips.
- **📑 Downloadable Executive PDF Reports**:
  - Generates professional executive PDF reports using `jsPDF` and `jspdf-autotable`.
  - Includes dataset health score, executive summary metrics, automated findings, and numeric statistical distributions.
  - Export filtered datasets directly as CSV.

---

## 🏗️ Architecture & Tech Stack

```
conversational_data_analysis/
├── backend/                  # FastAPI Backend Service
│   ├── main.py               # REST API endpoints, CORS, static SPA hosting
│   ├── data_engine.py        # Pandas data profiling, filtering, statistics & EDA
│   ├── ai_engine.py          # Gemini / OpenAI LLM integration & Smart Local Fallback
│   └── sample_data.py        # Curated sample datasets generator
├── frontend/                 # React 19 Frontend
│   ├── src/
│   │   ├── components/       # Navbar, ChatView, DatasetView, ChartStudio, ReportView
│   │   ├── utils/            # jsPDF PDF report exporter
│   │   ├── api.js            # Frontend API client
│   │   └── App.jsx           # Main application shell
│   ├── package.json          # Vite + React + Tailwind v4 + Chart.js + Lucide
│   └── vite.config.js        # Vite build & proxy configuration
├── samples/                  # Generated sample CSV datasets
├── run_app.py                # Unified one-command launcher
├── test_server.py            # Automated 7-point end-to-end test suite
├── Dockerfile                # Multi-stage production container build
└── docker-compose.yml        # Docker compose service definition
```

---

## 🚀 Quick Start Guide

### Prerequisites
- Python 3.10+
- Node.js 18+ and npm

### 1. One-Click Launch (Unified Mode)
Run the master launcher which builds the frontend and serves everything seamlessly:
```bash
python run_app.py
```
Or on Windows, simply double-click `start.bat`!
The app will automatically launch in your browser at `http://localhost:8000`.

### 2. Development Mode (with Hot Reloading)

**Terminal 1 — Backend:**
```bash
cd backend
python -m uvicorn main:app --reload --port 8000
```

**Terminal 2 — Frontend:**
```bash
cd frontend
npm run dev
```
Open `http://localhost:5173` for instant hot module reloading.

---

## 🧪 Running the End-to-End Test Suite

Verify that all 7 core subsystems (health check, profile, statistics, table querying, NLP chat engine, custom visualizer, and SPA hosting) work end-to-end:
```bash
python test_server.py
```

Expected output:
```
✓ Health check OK: {'status': 'ok', 'app': 'DataNova AI', 'active_datasets': 1}
✓ Profile OK: 600 rows, 13 columns
✓ Summary OK: Automated insights generated
✓ Table Query OK: returned 5 rows of 600
✓ Chat Query OK: Chart=bar, KPIs=3
✓ Visualize OK: Labels=['Middle East', 'Asia-Pacific', 'Latin America', ...]
✓ Frontend SPA HTML serving OK!
🎉 ALL 7 END-TO-END TESTS PASSED WITH 100% SUCCESS!
```

---

## 🌐 Production Deployment

### Docker Deployment
```bash
docker compose up --build -d
```
The application will be accessible on port 8000.

### Cloud Deployment (Render, Railway, Fly.io, Cloud Run)
- Use the included multi-stage `Dockerfile`.
- Set environment variables:
  - `PORT=8000`
  - `GEMINI_API_KEY` (optional)
  - `OPENAI_API_KEY` (optional)

---

## 🔒 Security & Privacy
- Files uploaded to DataNova AI are parsed in-memory and contained within your local session.
- Safe Pandas execution prevents unsafe eval loops.
- API keys can be entered directly in the UI Settings modal and are stored exclusively in the browser's `localStorage`.
