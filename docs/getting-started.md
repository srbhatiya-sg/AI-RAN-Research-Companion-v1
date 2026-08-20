# Getting Started

This guide walks through setting up the local AI environment for the **AI-RAN Research Companion** using AnythingLLM, Ollama, and Qwen3 8B.

---

## 1. Install Ollama

Download and install Ollama from its [official website](https://ollama.com).

After installation, verify the installation:

```powershell
ollama --version

```

## 2. Install Qwen3 8B

Download the model through Ollama:

```powershell
ollama pull qwen3:8b

```
Verify that the model is available:

```powershell
ollama list

```

## 3. Install AnythingLLM Desktop
Install [AnythingLLM Desktop](https://anythingllm.com/?utm_source=copilot.com) and launch the application.

## 4. Connect AnythingLLM to Ollama
In AnythingLLM, configure:

### AI Provider → LLM → Ollama

Select:
```powershell
qwen3:8b
```
At this point, AnythingLLM is using Ollama to run Qwen3 locally.

## 5. Create the Research Workspace
Create a new AnythingLLM workspace:

### AI-RAN Research Companion
This workspace will be used to organize and interact with your research documents

## 6. Add a Research Papers

Add a research paper(s) that you have obtained directly from its original publisher or source.

The paper is not included in this repository.
Users should obtain research papers directly from their respective publishers or organizations and add them to their own workspace.

## 7. Embed the Document
Allow AnythingLLM to process and embed the document(s) into the workspace.

Once embedding is complete, the document becomes available to the workspace for retrieval and analysis.

## 8. Verify the Setup

Ask a simple question about the document, for example:
```powershell
What is the main problem addressed by this paper?
```
If AnythingLLM retrieves relevant content and Qwen3 generates a response, the basic local AI environment is ready.

For the structured research methodology, continue to Research Workflow.


