# FAQ-Chat-Bot-With-AWS-Lex-Bot
A great beginner project using **AWS Lex Bot** and basic Python is creating a **Chatbot for FAQs or Order Placement**. This project will give you experience in building conversational interfaces, integrating them with backend services, and managing basic AWS services. I used this same method to create a chatbot to help end users place orders for a hypothetical company that offers clients software as a service or company laptops. 

### Project: **Simple FAQ Chatbot**
**Objective:** Create a chatbot to place client orders using AWS Lex and Python.

---

### Steps to Build:
#### 1. **Set up the AWS Lex Bot**
   - **Go to AWS Lex Console**: Create a new Lex bot.
   - **Configure the bot**:
     - **Bot Name**: `OrderBot`.
     - **Language**: English (or another language if preferred).
     - **Output voice**: None (for a text-based bot).
   - **Define Intents**:
     - Example:
       - `Place orders`: Create orders for customers.
     ![Intent Details](https://github.com/user-attachments/assets/71ed2724-25f4-47c3-9a95-40a569cb089c)

     - Add example utterances for each intent, e.g., "I would like to place an order" or "How can I order?"
    ![Sample Uterances](https://github.com/user-attachments/assets/f0da62b9-52cc-4049-abbc-b17eb9df5a85)

     
   - **Response Slots**:
     - Add simple text responses for each intent. By going to the slot menu and select "Add Slot" and choose Add blank slot type. After you can define your responses to the intent. I choose restrict to slot values due to the company only offering
       select services. You can define the slot type values by entering the word of the itme such as "Subscription" or "Laptop". Once they are set to your needs save the slot and navigate back to your Order Bot.
       
       ![slot values](https://github.com/user-attachments/assets/78401843-f395-4f60-b689-0e4be47695c8)

- **Setup Slots For Your Intent**:
In order for your Lex Bot to understand what information is needed in order to fufill the intent. You must create your slot and specify the data you are looking for since we have created our slot permatirs it should be listed
under slot type. And you may prompt the user for information.

  ![Capture](https://github.com/user-attachments/assets/0b40e585-761c-4f3d-b69e-e2adc00d43aa)

  I created two more slots to gather the users name and ask for them to define which subscription service they wanted. Yearly, Monthly ECT.
  ![all slots](https://github.com/user-attachments/assets/e666e46f-8d39-4c76-88f6-03ed5835f241)

- **Intent Confirmation**:
Once you have created all your slot respomnses specify your confirmation promp to the user. I chose "Great to meet you, {YourName}. Your {ProductType} order has been placed!". But you can enter anythging that will let your user know the bot acknoledges the requested task or information as completed.
![confirmation](https://github.com/user-attachments/assets/aaa99098-0941-466f-ae59-e5f5a66791e5)

- **Test Your ChatBot**:
- Once you have finished creating your bot select build this may take several minutes to finish once it is completed it will offer you to test it. Prompt the bot with your sample utterances if it responds according to plan then you are ready to deploy your bot!
  Here is my test responses and an overview of how it is mapped in the Visual Builder.
 ![Test case](https://github.com/user-attachments/assets/91795d26-21b6-40f4-8591-c5346c765f6c)

![order confirmation](https://github.com/user-attachments/assets/b15e5f21-84b8-4f06-afb0-a593472e0bb9)


![overview](https://github.com/user-attachments/assets/0b1c882c-3979-48fa-92b0-7b449a84ceff)



#### 2. **Create a Python Script**
Another way to interact with the bot to test if it works is by using a Python script. 
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

#### 3. **Run the Script**
   - Run the Python script, and the chatbot will respond to your inputs.

---

### Ideas to Extend
- **Add more intents**: Expand the bot to answer more types of questions.
- **Connect to a database**: Store and retrieve FAQ data dynamically.
- **Host on AWS Lambda**: Make it serverless and integrate with other AWS services.
- **Integrate with a front-end**: Use platforms like Amazon Connect or integrate with a web page or mobile app.

This project is simple enough to start with but provides lots of opportunities for learning and scaling!
