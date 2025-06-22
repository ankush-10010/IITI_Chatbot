# IITI_Chatbot

## Overview
IITI_Chatbot is an academic assistant and automation tool for IITI students and faculty. It can answer course-related queries, generate and solve question papers from PDFs, and create personalized schedules using LLMs and various AI APIs.

## Features
- Course query answering using semantic search and LLMs
- PDF question paper parsing and answer generation
- Daily and weekly schedule generation
- REST API with FastAPI

## Setup Instructions
1. Clone the repository.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Ensure you have the required API keys (Groq, OpenAI, Google Calendar, etc.) set as environment variables or in the code.
4. (Optional) For PDF/image processing, install system dependencies:
   - `poppler-utils` (for pdf2image)
   - `tesseract-ocr` (for pytesseract)

## Usage
Run the FastAPI server:
```bash
uvicorn query_question_schewoinput:app --reload
```

Send POST requests to `/route` with a prompt and (optionally) a PDF file.

## File Structure
- `query_question_schewoinput.py`: Main backend logic and API
- `requirements.txt`: Python dependencies

## Notes
- Some features require external API keys.
- For best results, use in a Linux environment for PDF/image tools.