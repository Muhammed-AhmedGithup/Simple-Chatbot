# Simple Chatbot

This project implements a basic conversational AI chatbot using the Hugging Face Transformers library and the `facebook/blenderbot-400M-distill` model.

## Features

*   **Conversational AI:** Engages in simple dialogue based on user input.
*   **Pre-trained Model:** Leverages the `blenderbot-400M-distill` model for efficient and effective responses.

## Setup and Installation

To run this chatbot, you need to have Python and `pip` installed. Follow these steps:

1.  **Clone the repository (if applicable):**
    ```bash
    git clone <your-repository-url>
    cd <your-repository-name>
    ```

2.  **Install the required libraries:**
    ```bash
    pip install transformers torch
    ```
    (Note: `torch` is a dependency of `transformers` for model execution.)

## How to Run

1.  **Import Libraries and Load Model:**

    The first step is to import the necessary classes from `transformers` and load the pre-trained model and tokenizer:
    ```python
    from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

    model = AutoModelForSeq2SeqLM.from_pretrained("facebook/blenderbot-400M-distill")
    tokenizer = AutoTokenizer.from_pretrained("facebook/blenderbot-400M-distill")
    ```

2.  **Define the Chatbot Function:**

    This function handles the continuous conversation with the bot. It takes user input, generates a reply, and prints it. The conversation ends when the user types 'bye', 'good bye', or 'see you letter'.
    ```python
    def chat_bot():
      while(True):
        text = input("You: ")
        if text in ['bye', 'good bye', 'see you letter']:
          break
        inputs = tokenizer(text, return_tensors='pt')
        reply_ids = model.generate(**inputs)
        out = tokenizer.decode(reply_ids, skip_special_tokens=True)
        print("Bot: ", out[0])
    ```

3.  **Start the Chatbot:**

    Simply call the `chat_bot()` function to start the conversation:
    ```python
    chat_bot()
    ```

## Example Interaction

```
You: hello
Bot:   Hello! How are you? I just got back from walking my dog. Do you have any pets?
You: can you speak arabic
Bot:   Yes, I can speak Arabic. It is the second most spoken language in the world after English.
You: ازيك
Bot:   Hello, do you speak any languages other than english? I speak french and english.
You: bye
```
