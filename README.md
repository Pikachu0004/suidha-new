## Community Hero

Community Hero is a hyperlocal issue reporting and resolution platform built around one principle: neighborhood problems should be easy to report, visible to track, and accountable to resolve.

It turns civic service into a community-first workflow where residents can report local issues quickly, escalate repeated problems, upload evidence, track progress with reference IDs, follow visible resolution status, and support action workflows through payments and records.

## Animated Project Summary

Community Hero combines a polished, motion-led interface with practical civic workflows so the product feels easy to use in real-world, shared-device settings. The current experience emphasizes clarity, transparency, multilingual access, voice support, and visible status tracking for every issue.

## Problem Statement Alignment

### Background

Communities frequently face potholes, water leakages, damaged streetlights, waste management concerns, and public infrastructure failures. Reporting these issues is often fragmented, difficult to track, and low in transparency.

### Challenge

Build a platform that enables citizens to identify, report, validate, track, and resolve community issues through collaboration, data, and intelligent automation. The solution should encourage transparency, accountability, and community participation.

### Evaluation focus

The solution should demonstrate how AI can help communities address local challenges more efficiently through improved reporting, verification, tracking, and resolution of issues.

## How This Project Answers The Challenge

Community Hero already implements the foundation of the challenge in a working product:

- structured issue reporting
- escalation logging for unresolved problems
- evidence upload
- reference-based issue tracking
- admin-side resolution dashboards
- voice-guided and multilingual access
- offline-safe queuing for key flows

It also includes platform hooks that support the next layer of intelligent automation:

- issue-type classification through category-driven flows
- evidence-aware validation workflows
- dashboard-ready operational data
- fraud and risk analysis patterns already used in the payment pipeline
- audit logging and device heartbeat signals that support trustworthy operations

## Current Product Preview

The current locally running version of the app has been aligned to the hyperlocal problem-solving theme with a resident-first dashboard, issue workflows, and resolution tracking.

## What Residents Can Do

Residents can use Community Hero to:

- report local issues such as potholes, water leakage, broken streetlights, and waste management concerns
- escalate repeated problems when an issue needs stronger follow-up
- upload evidence such as issue photos, location proof, and supporting media or records
- track issue resolution with a reference ID
- access multilingual UI, voice guidance, voice-assisted field filling, on-screen keyboard and keypad support, high-contrast mode, manual light and dark themes, and idle privacy reset for shared-device environments

## What Resolution Teams Can Do

Authorized staff can use the admin area to:

- view incoming issue reports
- review escalations
- inspect attached evidence context
- update lifecycle statuses
- track operational activity
- monitor dashboards and health
- close resolved or rejected records

## Feature Mapping Against The Problem Statement

### Implemented now

- structured issue reporting
- hyperlocal issue categories
- escalation workflow
- real-time status lookup by reference ID
- evidence upload workflow
- impact and operations dashboards
- voice and accessibility support
- offline queueing for unstable connectivity

### Partially represented or ready for extension

- AI-powered issue categorization: category-driven reporting is in place and can be upgraded with model-based classification
- community verification: escalation and evidence workflows are present and can evolve into resident verification loops
- predictive insights: dashboards, audit data, and issue metadata are available for future trend and hotspot analysis
- gamification for citizen engagement: not implemented yet, but the user and activity structure is available for a future participation layer
- geo-location and mapping: not implemented yet in the current frontend, but the reporting flow is ready for map and location capture expansion

## UX Direction

The frontend uses a premium retro neo-brutalist dashboard style so the product feels memorable, visible, and accessible in shared community settings.

Design characteristics include:

- thick borders
- hard shadows
- paper-like surfaces
- pastel contrast system
- handwritten accent labels
- bold hierarchy
- responsive control sidebar
- polished light and dark themes

Key files:

- [frontend/src/index.css](frontend/src/index.css)
- [frontend/src/components/Layout.jsx](frontend/src/components/Layout.jsx)
- [frontend/src/context/LanguageContext.jsx](frontend/src/context/LanguageContext.jsx)
- [frontend/src/pages/Home.jsx](frontend/src/pages/Home.jsx)

## User Flows

### Resident flow

1. Open the welcome screen.
2. Select a language.
3. Log in with OTP or continue in guest mode.
4. Choose one of the main actions: report issue, escalate issue, upload evidence, support payment, or track issue.
5. Save the generated reference ID.

### Resolution team flow

1. Open team login.
2. Sign in using mobile and password.
3. Verify the OTP challenge.
4. Review issue reports and escalations.
5. Update statuses and monitor dashboards.

## Screens In The Current App

### Resident-facing

- `/` welcome screen and community overview
- `/chat` civic companion chat flow
- `/services` service discovery flow
- `/complaints` local issue reporting and escalation flow
- `/documents` document guidance flow

## Architecture Overview

### Tech Stack

#### Frontend

- React 19
- React Router DOM 7
- Tailwind CSS 3
- Framer Motion
- Lucide React
- Axios

#### Backend

- FastAPI
- MongoDB via Motor
- Google Gemini integration
- JWT-style auth patterns and API-ready service endpoints

### Repository Structure

```text
.
├── backend/
│   ├── requirements.txt
│   └── server.py
├── frontend/
│   ├── public/
│   └── src/
│       ├── components/
│       ├── context/
│       ├── hooks/
│       ├── lib/
│       └── pages/
├── design_guidelines.json
├── PITCH_SCRIPT.md
├── README.md
├── test_result.md
└── tests/
```

## Local Development

### Prerequisites

- Node.js 18+
- npm 9+ or Yarn
- Python 3.10+
- MongoDB running locally or a MongoDB Atlas URI

### Backend setup

```bash
cd backend
pip install -r requirements.txt
# create backend/.env with:
# MONGO_URL="mongodb://localhost:27017"
# DB_NAME="community_hero"
# GEMINI_API_KEY="your-gemini-api-key"
uvicorn server:app --reload --port 8001
```

### Frontend setup

```bash
cd frontend
npm install
# create frontend/.env with:
# REACT_APP_BACKEND_URL=http://localhost:8001
```

### Run locally in two terminals

Terminal 1:

```bash
cd backend
uvicorn server:app --reload --port 8001
```

Terminal 2:

```bash
cd frontend
npm start
```

### Local URLs

- Frontend: http://localhost:3000
- Backend health: http://localhost:8001/api/health

## API Snapshot

Detailed endpoint notes live in backend/server.py.

Important routes:

- `POST /api/ai/chat`
- `POST /api/ai/chat/stream`
- `POST /api/complaints/submit`
- `GET /api/complaints/track/{ticket_id}`
- `POST /api/complaints/update-status`
- `GET /api/complaints/stats`

## Security And Trust Signals

- JWT-protected routes
- role-based access control
- OTP-driven auth flows
- rate limiting
- password hashing
- audit logging
- device heartbeat support
- consent-driven uploads

## AI And Intelligence Roadmap

To align more directly with the challenge, the strongest next upgrades would be:

- AI-powered issue categorization from text and uploaded evidence
- geo-tagging and map clustering of issue hotspots
- community validation loops for duplicate or repeated reports
- predictive dashboards for likely failure zones and recurring issue types
- gamified participation rewards for residents who submit strong evidence and valid reports

## Troubleshooting

### Port already in use

```bash
lsof -nP -iTCP:8001 -sTCP:LISTEN
lsof -nP -iTCP:3000 -sTCP:LISTEN
```

### Missing backend environment variables

```bash
cd backend
export MONGO_URL="mongodb://localhost:27017"
export DB_NAME="community_hero"
export GEMINI_API_KEY="your-gemini-api-key"
```

### Backend fails on startup

```bash
cd backend
pip install -r requirements.txt
```

### Frontend dependency issue with Rollup optional native package

```bash
rm -rf frontend/node_modules frontend/package-lock.json
cd frontend
npm install
```

## Additional Docs

- [PITCH_SCRIPT.md](PITCH_SCRIPT.md)
- [test_result.md](test_result.md)
- [design_guidelines.json](design_guidelines.json)
