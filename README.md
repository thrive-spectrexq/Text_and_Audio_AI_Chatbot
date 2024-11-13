# Text and Audio AI Chatbot

This repository contains two simple python scripts for creating interactive AI chatbots using OpenAI's GPT-3.5-turbo model. One chatbot interacts through text, and the other through audio. The text-based chatbot uses Gradio for the user interface, while the audio-based chatbot uses OpenAI's Whisper model for transcription and `pyttsx3` for text-to-speech.

## Setup

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/thrive_spectrexq/Text_and_Audio_AI_Chatbot.git
   cd Text_and_Audio_AI_Chatbot

2. **Install Dependencies:**
  - Make sure you have Python 3.x installed. Then, install the required packages:
    ```bash
    pip install -r requirements.txt

3. **Set Up Environment Variables:**
  - Create a .env file in the root of the project and add your OpenAI API key:
    ```bash
    OPENAI_API_KEY = "your_openai_api_key"

4. **How to run:**
    ```bash
    python app.py
    python appaudio.py
