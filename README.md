# ChatBoT
SImple machine learning 
import re

# Define some basic responses
responses = {
    r"(hello|hi|hey)": "Hello! How can I assist you?",
    r"what is your name": "I am a simple chatbot.",
    r"how are you": "I'm good, thank you!",
    r"(.+) your name(.+)": "My name is ChatBot.",
    r"(.+) (weather|temperature) (.+)": "I'm sorry, I am not able to provide weather information at the moment.",
    r"(.+) (help|support)": "Sure! I am here to help. How can I assist you?",
    r"(.+) (bye|goodbye)": "Goodbye! Have a great day!",
    r"(.+)": "I'm sorry, I don't have an answer for that at the moment.",
}

def chatbot_response(user_input):
    for pattern, response in responses.items():
        match = re.search(pattern, user_input, re.IGNORECASE)
        if match:
            return re.sub(pattern, response, user_input, flags=re.IGNORECASE)
    return "I'm sorry, I don't have an answer for that at the moment."

if __name__ == "__main__":
    print("ChatBot: Hello! How can I assist you?")
    while True:
        user_input = input("You: ")
        if user_input.lower() in ["exit", "quit", "bye"]:
            print("ChatBot: Goodbye! Have a great day!")
            break
        response = chatbot_response(user_input)
        print("ChatBot:", response)
