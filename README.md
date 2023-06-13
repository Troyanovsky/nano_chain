# NanoChain Library Documentation
NanoChain is a Python library designed to provide a suite of useful tools for text processing, vector indexing, and utilizing OpenAI's GPT-3.5-turbo model to perform various tasks.

## Features
GPT-3.5-turbo API integration
Summary buffer memory for conversation summarization
Text file and PDF file loader
Text splitting for large texts
Vector indexing using the ChromaDB library
ReActAgent for performing tasks using available tools

## Installation
To install:
```
pip install nanochain
```

## Usage
In order to use the NanoChain library, import it into your Python script as shown below:
```
import nanochain
```

### GPT-3.5-turbo API integration
The get_API_Response function is used to interact with the GPT-3.5-turbo API. It sends a prompt and returns the response from the model.

Example usage:
```
response = nanochain.get_API_Response("What is the capital of France?")
print(response)
```

### SummaryBufferMemory
The SummaryBufferMemory class is used to store and summarize a conversation. It can be initialized with an optional word_limit parameter.

Example usage:
```
summary_buffer = nanochain.SummaryBufferMemory(word_limit=1000)
```

### File loader
The file_loader function is used to load text from a PDF or text file. The function returns the extracted text as a string.

Example usage:
```
text = nanochain.file_loader("document.pdf")
print(text)
```

### Text splitting
The text_splitter function is used to split a large text into smaller sections, optionally with a specified overlap between sections.

Example usage:
```
sections = nanochain.text_splitter(text, n_words=500, overlap=50)
print(sections)
```

### Vector indexing
The vectorIndex class is used for indexing and querying text documents using the ChromaDB library.

Example usage:
```
vector_index = nanochain.vectorIndex(documents=["Document 1", "Document 2"])
vector_index.add_documents(documents=["Document 3", "Document 4"])
results = vector_index.query_documents(query_string="Search query")
print(results)
```

### ReActAgent
The ReActAgent class is designed to perform tasks using available tools. You can add or remove tools, and run the agent with a given task string.

Example usage:
```
agent = nanochain.ReActAgent(verbose=True, max_steps=10)
agent.add_tool(("New tool", "New tool description", function_name))
agent.remove_tool("New tool")

task_string = "Find the capital of France."
result = agent.run(task_string)
print(result)
```
