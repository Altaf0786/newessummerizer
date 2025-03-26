### Architecture Diagram

![92689DBB-0393-452C-BD5F-F9A5A03B8150](https://github.com/user-attachments/assets/480b5eb1-c525-478d-ba40-c2d73fabc91a)


# 📚 BBC News Summarizer & Sentiment Analyzer

The **BBC News Summarizer & Sentiment Analyzer** is an intelligent web application designed to help users quickly digest large volumes of BBC news content. By entering a BBC topic URL or keyword, users can fetch multiple related articles, summarize them into concise snippets using powerful AI models, and analyze the overall sentiment of the coverage. This application leverages cutting-edge technologies such as the **GROQ API** and **LangChain** for summarization and sentiment analysis.

---

## 📝 Introduction

This application is built to serve as a tool for researchers, media analysts, and curious readers who want to interpret news sentiment patterns and quickly understand the essence of lengthy articles. It provides a user-friendly interface using **Streamlit** and **FastAPI**, with seamless integration of AI capabilities.

---

## 🔎 Key Features

### Core Features:
- **Automatic Article Scraping:** Fetch BBC articles based on keywords or URLs.
- **AI-Powered Summarization:** Generate concise summaries using GROQ LLM models.
- **Sentiment Analysis:** Analyze the sentiment (positive, negative, neutral) of each article.
- **Topic Extraction:** Identify common keywords and themes across articles.
- **Article Comparisons:** 
  - Auto Comparison: Sentiment-based comparisons between articles.
  - Manual Comparison: Side-by-side comparison for in-depth analysis.
- **Hindi Sentiment Summary:** Sentiment summaries translated into Hindi for broader accessibility.

### Technical Features:
- Built with **FastAPI** and **Streamlit** for a robust backend and user-friendly frontend.
- Integrated with **LangChain** for advanced AI functionalities.
- Supports **GROQ API(llama-3.3-70b-versatile model)** for high-performance AI operations.

---

## 🎯 Project Goals

- **Sentiment Bias Detection:** Identify tone and bias in BBC's coverage of specific topics or companies.
- **Efficient Summarization:** Provide quick summaries of lengthy articles using AI.
- **Comprehensive Analysis:** Empower users to interpret sentiment patterns across multiple articles or timeframes.
- **User-Friendly Interface:** Deliver a smooth experience with **Streamlit** and **FastAPI**.

---

## 🚀 Tech Stack

| **Layer**            | **Technology**                                                    |
|----------------------|------------------------------------------------------------------|
| **Backend**          | FastAPI, BeautifulSoup, LangChain                               |
| **LLM**              | GROQ API (using **Mixtral** or **LLaMA2** models via LangChain) |
| **Frontend**         | Streamlit                                                       |
| **NLP Features**    | LangChain Summarization + Sentiment Analysis + gtts                   |

---

## ⚡ Alternative Setup (Optional)

If you do not have access to **GROQ API**, you can modify the application to use **Hugging Face Transformers** models:

- **Summarization:** Using `facebook/bart-large-cnn`
- **Sentiment Analysis:** Using the `sentiment-analysis` pipeline from Hugging Face

### Example Usage:
```python
from transformers import pipeline

summarizer = pipeline("summarization", model="facebook/bart-large-cnn")
sentiment_analyzer = pipeline("sentiment-analysis")
```

---

## 📚 API Documentation

### 1. GET `/`
- **Description:** Returns a simple confirmation string.
- **Response:**
  ```json
  "string"
  ```

### 2. GET `/health`
- **Description:** Checks if the service is running.
- **Response:**
  ```json
  "Service is healthy"
  ```

### 3. POST `/analyze/`
- **Description:** Analyzes news articles for a specific keyword/company across multiple pages.
- **Request Body:**
  ```json
  {
    "query": "apple",
    "start_page": 1,
    "end_page": 3,
    "lines": 3
  }
  ```
- **Parameters:**
  | Parameter | Type | Description |
  | --- | --- | --- |
  | query | string | Keyword or company to search |
  | start_page | int | Starting page number |
  | end_page | int | Ending page number |
  | lines | int | Number of summary lines per article |

- **Example cURL:**
  ```bash
  curl -X 'POST' \
    'http://localhost:8000/analyze/' \
    -H 'accept: application/json' \
    -H 'Content-Type: application/json' \
    -d '{
      "query": "apple",
      "start_page": 1,
      "end_page": 3,
      "lines": 3
    }'
  ```

- **Example Response:**
  ```json
  {
    "success": true,
    "result": {
      "Company": "apple",
      "Articles": [
        {
          "Title": "Apple takes legal action in UK data privacy row",
          "Published Date": "4 March 2025",
          "Summary": "Apple has taken legal action to challenge...",
          "Sentiment": "Neutral",
          "Topics": [
            "Apple",
            "Advanced Data Protection",
            "Investigatory Powers Tribunal"
          ],
          "Link": "https://www.bbc.co.uk/news/articles/c8rkpv50x01o"
        }
      ]
    }
  }
  ```

---

## ⚙️ Project Setup

### 1. Clone the Repository
```bash
git clone https://github.com/Altaf0786/newessummerizer.git
newessummerizer
```

### 2. Create a Virtual Environment
```bash
python -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Configure API Keys
Create a `.env` file in the project root:
```env
GROQ_API_KEY=your_groq_api_key_here
```

### 5. Run the FastAPI Server
```bash
uvicorn api:app --reload
```

### 6. Run the Streamlit App (Optional)
```bash
streamlit run app.py
```



## 📦 Dependencies

The project requires the following dependencies, listed in `requirements.txt`:
```text
fastapi
uvicorn
streamlit
beautifulsoup4
requests
langchain
httpx
pydantic
seaborn
matplotlib
transformers
torch
tqdm
groq
scikit-learn
nltk
spacy
yaml
```

---

This README provides a comprehensive overview of the project, its features, and how to set it up. For further details or contributions, please refer to the GitHub repository.
