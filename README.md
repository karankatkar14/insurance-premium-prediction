# Insurance Premium Category Prediction

An end-to-end Machine Learning project that predicts an insurance premium category based on user information. The application combines a trained Scikit-learn model, a FastAPI backend, and a Streamlit frontend, with Docker support for deployment.

## Project Overview

This project allows users to enter personal and lifestyle-related details and receive a predicted insurance premium category along with prediction confidence and class probabilities.

## Features

- Machine Learning-based insurance premium category prediction
- Interactive Streamlit user interface
- FastAPI REST API
- Input validation using Pydantic
- Prediction confidence and class probabilities
- Health-check endpoint
- Automatic API documentation using Swagger UI
- Docker containerization
- Docker Hub image available
- AWS EC2 deployment workflow

## Tech Stack

- **Language:** Python
- **Machine Learning:** Scikit-learn
- **Data Processing:** Pandas, NumPy
- **Backend:** FastAPI, Uvicorn
- **Validation:** Pydantic
- **Frontend:** Streamlit
- **Containerization:** Docker
- **Cloud Deployment:** AWS EC2
- **Version Control:** Git and GitHub

## Project Structure

```text
insurance-premium-prediction/
├── config/
│   └── city_tier.py
├── model/
│   ├── model.pkl
│   └── predict.py
├── schema/
│   ├── prediction_response.py
│   └── user_input.py
├── app.py
├── frontend.py
├── requirements.txt
├── Dockerfile
├── insurance.csv
├── fastapi_ml_model .ipynb
├── .gitignore
└── README.md
```

## Application Workflow

1. The user enters information in the Streamlit interface.
2. Streamlit sends the input to the FastAPI prediction endpoint.
3. FastAPI validates the request using Pydantic.
4. The application prepares the required model features.
5. The trained Machine Learning model generates a prediction.
6. The API returns the predicted category, confidence, and class probabilities.
7. Streamlit displays the prediction to the user.

## Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/karankatkar14/insurance-premium-prediction.git
cd insurance-premium-prediction
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it on Windows:

```powershell
.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Start the FastAPI backend

```bash
uvicorn app:app --reload
```

API base URL:

`http://127.0.0.1:8000`

Swagger documentation:

`http://127.0.0.1:8000/docs`

Health check:

`http://127.0.0.1:8000/health`

### 5. Start the Streamlit frontend

Open a second terminal, activate the same virtual environment, and run:

```bash
streamlit run frontend.py
```

Open:

`http://localhost:8501`

Ensure the FastAPI backend is running before requesting a prediction.

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/` | API welcome message |
| GET | `/health` | API and model health status |
| POST | `/predict` | Predict insurance premium category |

Use Swagger UI at `/docs` to inspect the request schema and test the prediction endpoint.

## Docker

Build the Docker image:

```bash
docker build -t insurance-premium-api .
```

Run the API container:

```bash
docker run -d --name insurance-api -p 8000:8000 insurance-premium-api
```

Check running containers:

```bash
docker ps
```

View container logs:

```bash
docker logs insurance-api
```

## Docker Hub

Docker Hub image:

`karankatkar/insurance-premium-api:latest`

Pull the image:

```bash
docker pull karankatkar/insurance-premium-api:latest
```

Run the API:

```bash
docker run -d --name insurance-api -p 8000:8000 karankatkar/insurance-premium-api:latest
```

## AWS Deployment

The FastAPI backend can be deployed on an AWS EC2 instance using Docker.

Deployment workflow:

```text
Machine Learning Model
        ↓
FastAPI Backend
        ↓
Docker Image
        ↓
Docker Hub
        ↓
AWS EC2
        ↓
REST API
        ↓
Streamlit Frontend
```

For remote access, configure the EC2 security group carefully and allow only the required inbound traffic. Do not expose secrets or credentials in the repository.

## Future Improvements

- Deploy the Streamlit frontend publicly
- Add automated tests
- Implement CI/CD using GitHub Actions
- Add structured logging and monitoring
- Improve model evaluation and performance
- Use environment variables for API configuration
- Add API authentication where appropriate

## Author

**Karan Katkar**

B.E. Information Technology

Interests: Machine Learning, Data Science, Artificial Intelligence, and Backend Development.

## Disclaimer

This project is intended for educational and demonstration purposes. Predictions are model-generated estimates and should not be treated as official insurance quotations or financial advice.
