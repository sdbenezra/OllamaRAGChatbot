# Local RAG with Ollama

This project allows you to run Retrieval-Augmented Generation (RAG) with a model on your local machine using Ollama.
You can also run this project from Google Colab using Ngrok to publish to a public URL. Details are below. Running from Colab is an easy and
free way to test out a RAG setup, Colab has a limited run time. For a more permanent solution deploy to a server (process not
covered here, it depends on the service used).

Start with the instructions for this project here: [video](https://www.youtube.com/watch?v=kfbTZFAikcE),
[written](https://www.linkedin.com/pulse/how-build-rag-chatbot-using-ollama-serve-llms-locally-sri-laxmi-beapc/?utm_source=share&utm_medium=member_ios&utm_campaign=share_via).
I've added detailed additional instructions below to clarify some of the steps.

Ollama reference: https://github.com/ollama/ollama?tab=readme-ov-file

## Installing Ollama on MAC
- download ollama from the website https://ollama.com/download
- unzip the downloaded package and move the unzipped package to Applications
- launch Ollama from Applications - it will prompt you to install the cli

## Downloading a model to work with
- at a terminal run `ollama pull <model>` - replace with the model name you want to use.
  - `ollama run <model>` runs the model for querying in the terminal.

## Requirements for this project

### Create your virtual environment and add an app.py file

Enter the code as shown in the repository

### Run the following in the terminal

`ollama pull nomic-embed-text`

`pip install BeautifulSoup4`

`pip install tiktoken`

`pip install chromadb`

### To create a requirements file

`pip freeze > requirements.txt`

### Start ollama server
`ollama run <model>`

### Run your streamlit app
`streamlit run <your app>`

##### Ollama tips
To check if ollama is running pull up `localhost:11434` in the browser. 
It should respond with `Ollama is running`

Query Ollama via curl in the terminal:
`curl http://localhost:11434/api/chat -d '{
  "model": "mistral",
  "messages": [
    { "role": "user", "content": "How many countries have nuclear power plants" }
  ], "stream": false
}'`

Leave out the "stream" option or set to `true` in order to stream output.

Or you can enter `ollama run <model>` and enter a question at the prompt.

Enter `/bye` at the prompt in the terminal or CTRL-C to quit your Ollama server.

## Running on Colab
Upload the Ollama.ipynb to Google Colab. The 'app.py' file can be uploaded to the Colab files section under `/content`.
To use the Ngrok service to create a public url, sign up for an account at `ngrok.com`. You can then set up an authtoken.
Add it as a notebook secret with the name `NGROKTOKEN` and the value as the token. Be sure to authorize its use in the notebook.
Run each cell in order and next to last cell should output the ngrok endpoint to use to access your app.