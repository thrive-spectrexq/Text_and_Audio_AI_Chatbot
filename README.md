# Text and Audio AI Chatbot

This repository contains two scripts for creating interactive AI chatbots using OpenAI's GPT-3.5-turbo model. One chatbot interacts through text, and the other through audio. The text-based chatbot uses Gradio for the user interface, while the audio-based chatbot uses OpenAI's Whisper model for transcription and `pyttsx3` for text-to-speech.

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
   git clone https://github.com/yourusername/Text_and_Audio_AI_Chatbot.git
   cd Text_and_Audio_AI_Chatbot

2. **Install Dependencies:**
  - Make sure you have Python 3.x installed. Then, install the required packages:
  - pip install openai gradio pyttsx3 python-dotenv

3. **Set Up Environment Variables:**
  - Create a .env file in the root of the project and add your OpenAI API key:
  - OPENAI_API_KEY=your_openai_api_key

4. **Text-Based Chatbot**
  - Script: `text_chatbot.py`
  
import openai
import gradio as gr
import os
from dotenv import load_dotenv

load_dotenv()

openai.api_key = os.getenv("OPENAI_API_KEY")

messages = [
    {
        "role": "system",
        "content": "You are an AI Assistant specialized in Software Engineering and Cybersecurity.",
    },
]

def chatbot(input):
    if input:
        messages.append({"role": "user", "content": input})
        chat = openai.ChatCompletion.create(model="gpt-3.5-turbo", messages=messages)
        reply = chat.choices[0].message.content
        messages.append({"role": "assistant", "content": reply})
        return reply

inputs = gr.inputs.Textbox(lines=7, label="Chat with AI")
outputs = gr.outputs.Textbox(label="Reply")

gr.Interface(
    fn=chatbot,
    inputs=inputs,
    outputs=outputs,
    title="AI Chatbot",
    description="Enter your prompts here",
    theme="compact",
).launch(share=True)

5. **How to Run:**
   - python text_chatbot.py

6. **Audio-Based Chatbot**
   - Script: `audio_chatbot.py`

   import gradio as gr
import openai
import pyttsx3
from dotenv import load_dotenv
import os

load_dotenv()

openai.api_key = os.getenv("OPENAI_API_KEY")

messages = [{"role": "system", "content": "You are a teacher"}]

def transcribe(audio):
    global messages
    file = open(audio, "rb")
    transcription = openai.Audio.transcribe("whisper-1", file)
    print(transcription)
    messages.append({"role": "user", "content": transcription["text"]})
    response = openai.ChatCompletion.create(model="gpt-3.5-turbo", messages=messages)

    AImessage = response["choices"][0]["message"]["content"]
    engine = pyttsx3.init()
    engine.say(AImessage)
    engine.runAndWait()
    messages.append({"role": "assistant", "content": AImessage})
    chat = ""
    for message in messages:
        if message["role"] != "system":
            chat += message["role"] + ":" + message["content"] + "\n\n"
    return chat

ui = gr.Interface(
    fn=transcribe, inputs=gr.Audio(source="microphone", type="filepath"), outputs="text"
)

ui.launch()

7. **How to Run:**
   - python audio_chatbot.py

8. **Notes**
   - Ensure your OpenAI API key is correctly set in the .env file.
   - The text-based chatbot and audio-based chatbot can run independently.
   - Adjust the system role and other configurations as needed for your use case.

