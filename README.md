# FAQ Bot

## Project Overview

The goal of this project is to automate an FAQ bot that can answer user queries based on a predefined set of frequently asked questions (FAQs). The bot utilizes natural language processing and machine learning techniques to provide accurate and contextually relevant responses.

## Requirements

* Python 3.x
* Required libraries:
    * `langchain`
    * `langchain_community`
    * `langchain_groq`
    * `python-dotenv`
    * `faiss-cpu` (or `faiss-gpu` if using GPU)

You can install the required libraries using pip:

```bash
pip install langchain langchain_community langchain_groq python-dotenv faiss-cpu
```

## Setup Instructions

1. **Clone the Repository**

    ```bash
    git clone https://github.com/Bhavanam-Gireesh-Reddy/Automated-FAQ-Bot.git
    cd Automated-FAQ-Bot
    ```
2. **Create a `.env` File**
    Create a `.env` file in the root directory of the project to store any necessary environment variables.
3. **Prepare the FAQ Data**
    Create a `faq.json` file in the root directory with the following structure:

    ```json
    {
        "questions": [
            {
                "question": "What is your return policy?",
                "answer": "You can return any item within 30 days."
            },
            {
                "question": "How do I track my order?",
                "answer": "You can track your order using the tracking link sent to your email."
            }
        ]
    }
    ```
4. **Run the Application**
    Execute the script to start the FAQ bot:

    ```bash
    python Automated_FAQ_Bot.py
    ```

## Usage

Once the bot is running, you can interact with it through the console. Type your questions, and the bot will respond based on the FAQ data provided. To exit the conversation, type `exit` or `quit`.

### Example Interaction

```
Welcome to the FAQ Bot powered by Groq! Ask me anything. Type 'exit' to end.
You: What is your return policy?
Bot: You can return any item within 30 days.
You: How do I track my order?
Bot: You can track your order using the tracking link sent to your email.
You: exit
```

## Code Explanation

The main components of the code are as follows:

1. **Loading Environment Variables**: The `load_dotenv()` function loads environment variables from a `.env` file.
2. **Loading FAQ Data**: The code reads a JSON file (`faq.json`) containing questions and answers. It checks for the presence of the 'questions' key and handles potential errors such as file not found or JSON decoding issues.
3. **Document Splitting**: The `CharacterTextSplitter` is used to split the loaded documents into manageable chunks for processing.
4. **Creating Embeddings and Vector Store**: The `FastEmbedEmbeddings` class generates embeddings for the document chunks, which are then stored in a FAISS vector store for efficient retrieval.
5. **Building the Conversational Retrieval Chain**: The `ConversationalRetrievalChain` is created using the `ChatGroq` model, allowing the bot to retrieve answers based on user queries while maintaining conversational context.
6. **Starting the Conversation**: A loop is initiated to handle user input, retrieve answers from the bot, and maintain chat history.

## Error Handling

The code includes basic error handling for:

* Missing `faq.json` file
* Invalid JSON format in `faq.json`
* Malformed items in the JSON structure

## Conclusion

This README provides a comprehensive overview of the FAQ bot project, including setup instructions, usage examples, and a breakdown of the code functionality. Follow the instructions to set up and run your own automated FAQ bot.
