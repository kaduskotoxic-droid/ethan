pip install openai
pip install SpeechRecognition
pip install pyttsx3
pip install pyaudio


#code 
import speech_recognition as sr
import pyttsx3
import datetime

engine = pyttsx3.init()

def speak(text):
    print("Assistant:", text)
    engine.say(text)
    engine.runAndWait()

recognizer = sr.Recognizer()

def listen():
    with sr.Microphone() as source:
        print("Listening...")
        audio = recognizer.listen(source)

    try:
        command = recognizer.recognize_google(audio)
        print("You:", command)
        return command.lower()
    except:
        return ""

while True:

    command = listen()

    if "Hey Ethen" in command:
        speak("Hello, how can I help you?")

    elif "time" in command:
        time = datetime.datetime.now().strftime("%H:%M")
        speak("The time is " + time)

    elif "stop" in command:
        speak("Goodbye")
        break
