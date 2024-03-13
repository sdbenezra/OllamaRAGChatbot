# RAG with Ollama

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