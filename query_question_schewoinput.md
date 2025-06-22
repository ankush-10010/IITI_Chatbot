# Documentation: query_question_schewoinput.py

## Overview
This file implements the main backend logic for the IITI_Chatbot, including course query answering, question paper parsing/solving, and schedule generation. It exposes a FastAPI REST API for integration.

## Main Classes

### QueryBot
- Loads course data from a JSON file.
- Uses SentenceTransformer and FAISS for semantic search.
- Retrieves relevant course chunks and queries an LLM for answers.

### QuestionPaperBot
- Converts PDF question papers to images and extracts text using OCR.
- Generates answers or new question papers using LLMs.
- Can output formatted PDFs with answers.

### Scheduler
- Classifies user prompts as daily or weekly schedules.
- Builds prompts and parses LLM output to generate structured schedules.

### RouterAgent
- Classifies user prompts and routes them to the appropriate bot (QueryBot, QuestionPaperBot, Scheduler).
- Handles API key management and LLM calls.

## API Endpoints

### POST /route
- **Description:** Main entry point. Accepts a prompt and optional PDF file. Routes the request to the appropriate bot.
- **Parameters:**
  - `prompt` (str, required): User's query or instruction.
  - `file` (PDF, optional): PDF file for question paper parsing/solving.
- **Returns:**
  - JSON with `text` (answer or schedule) and optionally a `pdf_file` (as a stream).

## Dependencies
See `requirements.txt` for all required Python packages. System dependencies for PDF/image processing may be required (poppler-utils, tesseract-ocr).

## Usage Example
Run the FastAPI server:
```bash
uvicorn query_question_schewoinput:app --reload
```
Then send a POST request to `/route` with a prompt and (optionally) a PDF file. 