# 📊 Multimodal Financial Forecast

A web-based application that predicts financial time-series values using an LSTM model. Built with FastAPI and PyTorch, this tool supports both direct sequence input and `.csv` file uploads for batch forecasting.

---

## 🚀 Features

- 🔢 Input time-series data directly in the browser (JSON format).
- 📁 Upload `.csv` files for batch forecasting.
- 🧠 Powered by an LSTM model trained on financial datasets.
- ⚙️ FastAPI backend with templated HTML UI.
- 🐳 Dockerized for easy deployment.
- 🚢 Live deployable on Hugging Face Spaces.

---

## 🧠 How It Works

1. **User Input**: 
   - You can enter sequences directly or upload a `.csv` with your own data.

2. **Model Inference**:
   - The LSTM model is loaded from `pipeline/trained_models/`.
   - Input sequences are normalized and passed into the model.
   - The output is a forecast of future values.

3. **Output**:
   - The results are displayed directly on the webpage.
   - Graph removed (clean, console-style output).

---

## 🛠 Tech Stack

| Layer       | Tech        |
|-------------|-------------|
| Backend     | FastAPI     |
| ML Model    | PyTorch LSTM|
| Frontend    | HTML + CSS  |
| Deployment  | Docker + Hugging Face Spaces |

---

## 📂 Project Structure

multimodal-financial-forecast/
├── app/
│ ├── main.py # FastAPI backend
│ ├── templates/
│ │ └── index.html # User interface
│ └── static/
│ └── style.css # Stylesheet
│
├── pipeline/
│ ├── inference_pipeline.py # Model loading and inference
│ └── trained_models/
│ ├── lstm_forecaster.pt # Trained LSTM model
│ └── config.json # Input/output config
│
├── requirements.txt # Python dependencies
├── Dockerfile # Docker config
├── README.md # Project overview
└── .gitignore

## ✅ Requirements

Install dependencies locally (for testing):

```bash
pip install -r requirements.txt

## Run the app locally:

uvicorn app.main:app --reload

## 📁 Example CSV Format

Sample input file (for upload):

0.1,0.2,0.3,0.4,0.5
0.5,0.6,0.7,0.8,0.9


## 🐳 Docker Deployment

FROM python:3.10-slim

WORKDIR /app

COPY . .

RUN pip install --upgrade pip && pip install -r requirements.txt

EXPOSE 7860

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "7860"]


## Build and Run Locally

docker build -t multimodal-forecast .
docker run -p 7860:7860 multimodal-forecast
