# Setting Up Ollama in VS Code Notebook

### Step 1: Install Ollama
Downlaod and install from [ollama.com](https://ollama.com/download) for Windows/Mac/Linux. After install, Ollama run as a local server.

### Step 2: Pull a Free Llama Model
Here is the [list](https://ollama.com/library) of free models available in Ollama.
Install ollama in the terminal:
```
pip install ollama
```
Below is the example on how to pull a model in the terminal:
```
ollama pull llama3.2
ollama run llama3.2 "Hello!"
```
To run in the VS Code notebook cell:
```
import ollama

response = ollama.chat(
    model="llama3.2",
    messages=[{"role": "user", "content": "Explain Python generators briefly."}]
)
print(response["message"]["content"])
```
