# Text and Audio AI Chatbot

This repository contains two simple python scripts for creating interactive AI chatbots using OpenAI's GPT-3.5-turbo model. One chatbot interacts through text, and the other through audio. The text-based chatbot uses Gradio for the user interface, while the audio-based chatbot uses OpenAI's Whisper model for transcription and `pyttsx3` for text-to-speech.

## Features

- **Text-Based Chatbot**
  - Interactive text chat using OpenAI's GPT-3.5-turbo model.
  - Simple user interface with Gradio.
  - Customizable system role.

- **Audio-Based Chatbot**
  - Audio interaction using OpenAI's Whisper model for transcription.
  - Text-to-speech responses using `pyttsx3`.
  - Gradio interface for capturing audio input.
  - Customizable system role.

## Setup

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/thrive_spectrexq/Text_and_Audio_AI_Chatbot.git
   cd Text_and_Audio_AI_Chatbot

2. **Install Dependencies:**
  - Make sure you have Python 3.x installed. Then, install the required packages:
    ```bash
    pip install openai gradio pyttsx3 python-dotenv

**Set Up Environment Variables:**
  - Create a .env file in the root of the project and add your OpenAI API key:
    ```bash
    OPENAI_API_KEY = "your_openai_api_key"

**Text-Based Chatbot**
  - Script: `app.py`

**How to Run:**
  - python app.py

**Audio-Based Chatbot**
  - Script: `appaudio.py`

**How to Run:**
  - python appaudio.py

**Notes**
  - Ensure your OpenAI API key is correctly set in the .env file.
  - The text-based chatbot and audio-based chatbot can run independently.
  - Adjust the system role and other configurations as needed for your use case.

