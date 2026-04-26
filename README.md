# Automated Website Testing & Analytics Tool

## Author

**M.Sc. IT Final Year Project**
**Author:** Fareeduddin Shaikh
**Target Site:** https://the-internet.herokuapp.com

---

## Project Overview

A fully automated web testing tool built with Python and Selenium
that tests a target website for login functionality, form validation,
and visual errors. All results are stored in a SQLite database and
displayed on a live analytics dashboard with charts, metrics,
and CSV export.

---

## Features

| Feature | Description |
|---|---|
| Automatic login test | Selenium logs in and verifies success message |
| Form validation test | Detects correct error on empty form submission |
| Error tracking test | Scans pages for broken images and missing elements |
| Page load test | Verifies page title and load success |
| Analytics dashboard | Live web dashboard at localhost:5000/dashboard |
| Pass/Fail pie chart | Visual ratio of passed vs failed tests |
| Execution time chart | Bar chart showing speed of each test |
| Per-test breakdown | Avg, fastest, slowest per test across all runs |
| Run history | Full history of every test run with timestamps |
| CSV export | Download all results as a spreadsheet |
| Auto-refresh | Dashboard updates automatically every 60 seconds |
| Log files | Permanent dated log file for every run |
| Run ID system | Each run grouped by unique ID for traceability |

---

## Tech Stack

| Technology | Version | Purpose |
|---|---|---|
| Python | 3.10.2 | Core programming language |
| Selenium | 4.18.1 | Browser automation and testing |
| Flask | 3.0.0 | Web server and API backend |
| Flask-CORS | 4.0.0 | Cross-origin resource sharing |
| SQLite | Built-in | Database for storing results |
| Chart.js | 4.4.1 | Dashboard charts |
| pytest | 8.1.1 | Test runner |
| webdriver-manager | 4.0.1 | Auto ChromeDriver management |

---

## Project Structure

WebTestingProject/
├── app.py                  # Flask web server — 8 API routes
├── database.py             # SQLite database layer
├── logger.py               # Automatic log file system
├── config.py               # Central project configuration
├── run_all_tests.py        # Terminal test runner
├── requirements.txt        # Python dependencies
├── README.md               # This file
│
├── tests/
│   ├── test_page_load.py
│   ├── test_login.py
│   ├── test_form_validation.py
│   └── test_error_tracking.py
│
├── templates/
│   └── dashboard.html      # Analytics dashboard UI
│
├── static/
│   ├── dashboard.css       # Dashboard styles
│   └── dashboard.js        # Dashboard JavaScript
│
├── database/
│   └── test_results.db     # SQLite database file
│
└── logs/
└── test_log_YYYY-MM-DD.txt  # Daily log files

---

## Installation

**Step 1 — Clone or download the project:**
git clone https://github.com/YOUR_USERNAME/WebTestingProject.git
cd WebTestingProject

**Step 2 — Install all dependencies:**
pip install -r requirements.txt

**Step 3 — Option A: Run via terminal:**
python run_all_tests.py

**Step 3 — Option B: Run via dashboard:**
python app.py
Then open: `http://localhost:5000/dashboard`

---

## API Routes

| Method | Route | Description |
|---|---|---|
| GET | `/` | Server health check |
| GET | `/dashboard` | Analytics dashboard UI |
| GET | `/api/results` | All test results (JSON) |
| GET | `/api/results/<run_id>` | Results for one specific run |
| GET | `/api/summary` | Overall statistics |
| GET | `/api/runs` | All test runs |
| GET | `/api/export` | Download results as CSV |
| POST | `/api/run-tests` | Trigger a new test run |
| POST | `/api/clear` | Clear all data (dev only) |

---

## Dashboard Features

- **4 metric cards** — Total tests, Passed, Failed, Avg time
- **Status banner** — Green/amber/red based on pass rate
- **Pass/fail donut chart** — Visual ratio with tooltips
- **Latest run table** — Results for most recent run
- **Execution time bar chart** — Speed per test, colour coded
- **Per-test breakdown** — Historical avg/fastest/slowest
- **Run history table** — All past runs with pass rates
- **Run All Tests button** — Triggers Selenium from the browser
- **Export CSV button** — Downloads results as spreadsheet
- **Auto-refresh toggle** — Updates every 60 seconds

---

## Test Results

| Test | What it checks |
|---|---|
| Page Load Test | Homepage loads with correct title |
| Login Test | Valid credentials accepted, success message shown |
| Form Validation Test | Empty form correctly rejected with error |
| Error Tracking Test | Broken images detected and counted |

---

## Deployment

Deployed live at:
`https://YOUR-PROJECT-NAME.onrender.com`

*(URL updated after Week 6 deployment)*

---

## Database Schema

**Table: test_results**

| Column | Type | Description |
|---|---|---|
| id | INTEGER | Auto-increment primary key |
| run_id | TEXT | Links to parent run |
| test_name | TEXT | Name of the test |
| status | TEXT | PASSED or FAILED |
| passed | INTEGER | 1 = passed, 0 = failed |
| duration | REAL | Execution time in seconds |
| run_date | TEXT | Timestamp of test |
| description | TEXT | Pass/fail reason |

**Table: test_runs**

| Column | Type | Description |
|---|---|---|
| id | INTEGER | Auto-increment primary key |
| run_id | TEXT | Unique run identifier |
| started_at | TEXT | Run start timestamp |
| finished_at | TEXT | Run end timestamp |
| total | INTEGER | Total tests in run |
| passed | INTEGER | Tests that passed |
| failed | INTEGER | Tests that failed |
| duration | REAL | Total run time |
