# Eidolon S3 Rag Recipe

In this recipe we have created a RAG chatbot powered by documents living in s3.

The documents are parsed and embedded on the fly which is valuable if you have a small body
of data that may change frequently. To process a large body of data, you will want to set up an ingestion pipeline.

## Core Concepts
* Multi-agent communication
* Sub-component customization
* Dynamic embedding management

## Agents
### Conversational Agent
The user facing copilot. Ask this agent questions and it use the llm to provide answers while reaching out to the S3 
Search Agent as needed for relevant documents as needed assistance of the repo search agent.

### S3 Search Agent
Handles loading, embedding, and re-embedding documents ensuring they are up-to-date.

Translates queries into a vector search query and returns the top results.

## Directory Structure

- `resources`: This directory contains additional resources for the project. An example agent is provided for reference.
- `components`: This directory is where any custom code should be placed.

## Running the Server

First you need to clone the project and navigate to the project directory:

```bash
git clone https://github.com/eidolon-ai/eidolon-s3-rag.git
cd agent-machine
```

Then run the server using docker, use the following command:

```bash
make docker-serve
```

The first time you run this command, you may be prompted to enter credentials that the machine needs 
to run (ie, OpenAI API Key).

This command will download the dependencies required to run your agent machine and start the Eidolon http server in 
"dev-mode".

If the server starts successfully, you should see the following output:
```
Starting Server...
INFO:     Started server process [34623]
INFO:     Waiting for application startup.
INFO - Building machine 'local_dev'
...
INFO - Server Started in 1.50s
```
