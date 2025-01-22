# FAQ-Chat-Bot-With-AWS-Lex-Bot
A great beginner project using **AWS Lex Bot** and basic Python is creating a **Chatbot for FAQs or Customer Support**. This project will give you experience in building conversational interfaces, integrating them with backend services, and managing basic AWS services.

### Project: **Simple FAQ Chatbot**
**Objective:** Create a chatbot that answers frequently asked questions using AWS Lex and Python.

---

### Steps to Build:
#### 1. **Set up the AWS Lex Bot**
   - **Go to AWS Lex Console**: Create a new Lex bot.
   - **Configure the bot**:
     - **Bot Name**: `FAQBot`.
     - **Language**: English (or another language if preferred).
     - **Output voice**: None (for a text-based bot).
   - **Define Intents**:
     - Example:
       - `GetHours`: For business hours.
       - `GetLocation`: For location info.
     - Add example utterances for each intent, e.g., "What are your working hours?" or "Where are you located?"
   - **Response**:
     - Add simple text responses for each intent.

#### 2. **Deploy the Lex Bot**
   - Build the bot in the console.
   - Test it using the built-in testing window.

---

#### 3. **Create a Python Script**
   - Use the **Boto3** library to interact with the Lex bot.

##### Install Dependencies
```bash
pip install boto3
```

##### Example Python Code
```python
import boto3

# Create a Lex client
client = boto3.client('lex-runtime')

def chat_with_bot(user_input):
    response = client.post_text(
        botName='FAQBot',           # Replace with your bot name
        botAlias='Latest',          # Replace with your bot alias
        userId='user123',           # A unique user ID
        inputText=user_input        # The user input
    )
    return response['message']

if __name__ == "__main__":
    print("Welcome to FAQBot! Type 'exit' to quit.")
    while True:
        user_input = input("You: ")
        if user_input.lower() == 'exit':
            print("Goodbye!")
            break
        response = chat_with_bot(user_input)
        print(f"Bot: {response}")
```

---

#### 4. **Run the Script**
   - Run the Python script, and the chatbot will respond to your inputs.

---

### Ideas to Extend
- **Add more intents**: Expand the bot to answer more types of questions.
- **Connect to a database**: Store and retrieve FAQ data dynamically.
- **Host on AWS Lambda**: Make it serverless and integrate with other AWS services.
- **Integrate with a front-end**: Use platforms like Amazon Connect or integrate with a web page or mobile app.

This project is simple enough to start with but provides lots of opportunities for learning and scaling!
