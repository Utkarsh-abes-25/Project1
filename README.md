# PS04 — Personalized AI Learning Agent

A runnable CSE/Data Science educational project. It creates a personalized study plan from a learner's goals, available study time, self-rated skill levels and quiz results. It recommends the next topic using a transparent, explainable scoring model and tracks progress locally in JSON.

## Features
- Learner onboarding: goal, skill levels and weekly study time.
- Topic recommendation engine using skill gap, prerequisite readiness, quiz performance and estimated effort.
- Personalized weekly study plan.
- Quiz submission and mastery updates.
- Progress dashboard with topic-level mastery.
- FastAPI backend and responsive web interface.
- Transparent recommendation explanations.
- Local JSON persistence; no API key required.

## Tech stack
- Python 3.10+
- FastAPI + Uvicorn
- Vanilla HTML/CSS/JavaScript
- Rule-based recommendation model (explainable baseline)

## Run locally

```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate

pip install -r requirements.txt
uvicorn app.main:app --reload
```

Open http://127.0.0.1:8000

## Demo workflow
1. Open the dashboard.
2. Enter a learner name, learning goal and available weekly hours.
3. Adjust skill levels or keep the defaults.
4. Generate a personalized plan.
5. Complete a topic quiz and submit the score.
6. Review updated mastery and next recommendations.

## Recommendation logic
Each topic receives a score based on:
- Skill gap: lower mastery increases priority.
- Quiz performance: weak results increase revision priority.
- Prerequisite readiness: topics are recommended only when prerequisites are sufficiently mastered.
- Learning effort: estimated hours are considered against the learner's available time.

This is an explainable baseline recommender, not a trained predictive model. The project includes a clean location to replace or augment the scoring function with collaborative filtering, content-based ML, or a learned knowledge-tracing model.

## API
- `GET /api/health`
- `GET /api/catalog`
- `POST /api/profile`
- `GET /api/profile`
- `POST /api/plan`
- `POST /api/quiz`
- `GET /api/progress`

## Project structure
```text
app/
  main.py
  recommender.py
  data.py
  storage.py
  static/
    index.html
    styles.css
    app.js
data/
  catalog.json
  state.json
docs/
  PROJECT_REPORT.md
  DEMO_SCRIPT.md
```

## Limitations and future work
- Current learner data is stored locally in a JSON file; add authentication and a database for multi-user deployment.
- The recommender is a transparent heuristic baseline; evaluate ML alternatives using held-out learner interaction data.
- Quiz questions are demonstration questions and should be expanded and reviewed by subject experts.
- This prototype is an educational aid, not a substitute for instructors or formal assessment.
