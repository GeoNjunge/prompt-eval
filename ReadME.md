# PromptEval — AI-Powered Prompt Evaluation Platform

PromptEval is a full-stack system for evaluating, scoring, and managing prompt templates across domains such as software engineering, education, and content generation. The platform combines a deterministic regression-based scoring model with LLM-assisted analysis to produce structured, explainable evaluations.

## Architecture Overview

The system is designed as a hybrid evaluation pipeline:

* A custom-trained regression model (scikit-learn) provides deterministic scoring based on defined features (clarity, relevance, structure, etc.)
* LLM-based components assist with contextual understanding and prompt interpretation
* A FastAPI backend orchestrates evaluation workflows and API access
* An Angular frontend provides user interaction, management, and visualization

This hybrid approach ensures consistent scoring while leveraging LLM flexibility for contextual reasoning.

## System Components

### Frontend — Angular (v19)

* User authentication (login/register)
* Prompt template browsing and filtering
* Admin dashboard for managing templates
* Prompt evaluation interface with scoring output

### Backend — FastAPI (Python)

* RESTful API endpoints for authentication, templates, and evaluation
* Business logic for prompt scoring workflows
* Integration layer between frontend and AI services
* Data handling and persistence logic

### AI Evaluation Engine — Python (scikit-learn + LLM integration)

* Ridge regression model for deterministic prompt scoring
* Feature-based evaluation (clarity, specificity, context, relevance)
* JSON-based structured evaluation outputs
* Optional LLM-assisted processing for enhanced interpretation

## Project Structure

```
.
├── AI_model/
│   ├── scoring_artifacts/
│   ├── requirements.txt
│   └── DOCKERFILE
│
├── promptrag/
│   ├── api/
│   ├── core/
│   ├── models/
│   ├── schemas/
│   ├── services/
│   ├── utils/
│   └── server.py
│
└── promptEval/
    ├── src/app/
    ├── angular.json
    └── package.json
```

## Running the Project

### Frontend

```
cd promptEval
npm install
npm start
```

### Backend

```
cd promptrag
pip install -r requirements.txt
uvicorn server:app --reload
```

### AI Model

```
cd AI_model
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python scoring_artifacts/infer_ridge.py
```

## Evaluation Flow

1. User submits a prompt through the frontend
2. Frontend sends request to FastAPI backend
3. Backend processes input and forwards to evaluation engine
4. Regression model computes deterministic score
5. Optional LLM layer enhances contextual evaluation
6. Structured results are returned to frontend

## Deployment

* Frontend: Vercel
* Backend: Azure
* AI Model: Docker container

Ensure proper environment variable configuration and CORS handling across services.

## Key Design Focus

* Deterministic prompt evaluation using a regression-based model
* Hybrid architecture combining statistical models and LLM reasoning
* Modular backend for extensibility
* Separation of concerns between evaluation engine and API layer

## Author

George Njunge

## License

MIT License
