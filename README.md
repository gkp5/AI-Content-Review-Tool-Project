# AI Content Review Tool

A fast, scalable AI-powered content moderation API built with **FastAPI** and **Hugging Face Inference API**. This project moderates user-generated text to detect toxicity, hate speech, and inappropriate content, reducing false positives and improving moderation accuracy.

The API is hosted locally on Google Colab and exposed publicly with **ngrok** for easy testing and integration.

---

## 🚀 Features

* Uses Hugging Face open-source models (e.g., GPT-Neo, BERT, RoBERTa) for text classification
* Simple REST API built with FastAPI
* Publicly accessible via ngrok tunnel
* Easily testable with `POST /moderate` endpoint
* Example client code included for sending text and receiving moderation results
* Designed to be extensible for real-world social media and forum moderation

---

## 📋 Table of Contents

* [Demo](#demo)
* [Getting Started](#getting-started)
* [Usage](#usage)
* [Project Structure](#project-structure)
* [Environment Variables](#environment-variables)
* [Testing the API](#testing-the-api)
* [Troubleshooting](#troubleshooting)
* [Future Improvements](#future-improvements)

---

## Demo

Send a POST request to the `/moderate` endpoint with JSON payload:

```json
{
  "text": "I hate you and your kind!"
}
```

Example response:

```json
{
  "label": "toxic",
  "score": 0.9876
}
```

---

## Getting Started

### Prerequisites

* Python 3.8+
* Google Colab (recommended) or local environment
* Hugging Face API token ([Get yours here](https://huggingface.co/settings/tokens))
* Ngrok account and auth token ([Sign up here](https://ngrok.com/signup))

### Installation

1. Clone this repository:

```bash
git clone [https://github.com/yourusername/ai-content-review.git]
cd ai-content-review
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Set environment variables:

```bash
export HF_API_TOKEN="your_huggingface_api_token"
export NGROK_AUTH_TOKEN="your_ngrok_auth_token"
```

Or create a `.env` file:

```
HF_API_TOKEN=your_huggingface_api_token
NGROK_AUTH_TOKEN=your_ngrok_auth_token
```

4. Run the app:

```bash
python app.py
```

---

## Project Structure

```
├── app.py                 # FastAPI app and Hugging Face API integration
├── requirements.txt       # Python dependencies
├── README.md              # Project documentation
└── .env                   # Environment variables (ignored by git)
```

---

## Environment Variables

| Variable           | Description                               |
| ------------------ | ----------------------------------------- |
| `HF_API_TOKEN`     | Hugging Face API token for authentication |
| `NGROK_AUTH_TOKEN` | Ngrok authentication token for tunnel     |

---

## Testing the API

Use curl or Python requests to test:

```bash
curl -X POST https://your-ngrok-url/moderate -H "Content-Type: application/json" -d '{"text":"You are awesome!"}'
```

Or Python:

```python
import requests

url = "https://your-ngrok-url/moderate"
response = requests.post(url, json={"text": "You are awesome!"})
print(response.json())
```

---

## Troubleshooting

* **Ngrok auth error:** Make sure you set your ngrok token correctly.
* **Timeouts:** The Hugging Face model may take time on the first call; wait or try smaller inputs.
* **No response:** Check if FastAPI server is running and ngrok tunnel is active.
* **API key issues:** Verify your Hugging Face API token is valid and has inference permissions.

---

## Future Improvements

* Add support for batch moderation requests
* Use multiple models and ensemble predictions
* Add user authentication and rate limiting
* Deploy to a cloud platform (AWS, GCP, Azure)
* Build a frontend UI for manual moderation and review

---
