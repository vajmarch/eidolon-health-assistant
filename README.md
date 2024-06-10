# Eidolon S3 Rag Recipe

In this recipe we have created a RAG chatbot powered by documents living in s3

In this particular example, the documents are parsed and embedded on the fly. This is valuable if you have a small body
of data that may change frequently. To process a large body of data, you will want to set up an ingestion pipeline.

## Core Concepts
* Multi-agent communication
* Sub-component customization
* Dynamic embedding management

## Agents
### Repo Expert
The user facing copilot. Ask this agent questions about a repository, and it will go and find the answer with the
assistance of the repo search agent.

### Repo Search
Handles loading, embedding, and re-embedding documents ensuring they are up-to-date.

Translates queries into a vector search query and returns the top results.

## Directory Structure

- `resources`: This directory contains additional resources for the project. An example agent is provided for reference.
- `components`: This directory is where any custom code should be placed.

## Running the Server

To run the server in dev mode, use the following command:

```bash
export AWS_ACCESS_KEY_ID=<YOUR AWS ACCESS KEY>
export AWS_SECRET_ACCESS_KEY=<YOUR AWS SECRET ACCESS KEY>
make serve-dev
```

🚨 Make sure you sure you set `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` so you can access the s3 bucket.

This will start the Eidolon http server without MongoDB along with some other dev tools such as recordings.
