# Troubleshooting

This page captures some of the practical issues encountered while setting up the AI-RAN Research Companion with AnythingLLM, Ollama, and Qwen3 8B.

The examples are based on a Windows laptop setup. Your environment may behave differently.

---

## 1. Ollama Cannot Download the Model

### Symptom

Running:

```powershell
ollama pull qwen3:8b
```
may return an error similar to:

``` text
Error: pull model manifest:
Get "https://registry.ollama.ai/...":
dial tcp: lookup registry.ollama.ai: no such host
```
### What It Means

Ollama needs to connect to its model registry to download the model.

This type of error indicates that the computer was unable to resolve or reach the registry at that moment.

### Check DNS Resolution

Run:
``` powershell
nslookup registry.ollama.ai
```

If the command returns IP addresses, DNS resolution is working.

For example:
``` text
Name:    registry.ollama.ai
Addresses: ...
```
If DNS resolution works but ollama pull still fails, the problem may be related to network connectivity, DNS configuration, firewall filtering, or the network itself.

## 2. AnythingLLM Does Not Automatically Mean You Have Qwen3

AnythingLLM and Qwen3 serve different purposes.

The setup uses:

```test
AnythingLLM
    ↓
Workspace / document interaction
    ↓
Ollama
    ↓
Local model runtime
    ↓
Qwen3 8B
```
AnythingLLM is the application/workspace layer.

Ollama runs the local model.

Qwen3 is the language model.

Installing AnythingLLM does not mean that every model is automatically installed locally.

## 3. Qwen3 Is Installed, But AnythingLLM Cannot Use It

First check that Ollama can see the model:

``` powershell
ollama list
```
You should see:
```powershell
qwen3:8b
```

You can also test the model directly:
```powershell
ollama run qwen3:8b

````

If Qwen3 responds here, the model and Ollama runtime are working.

Then check the AnythingLLM configuration:

```text
AI Provider
    ↓
LLM
    ↓
Ollama
    ↓
qwen3:8b
```

Make sure the model selected in AnythingLLM matches the model installed in Ollama.

## 4. Large Documents Can Exceed the Available Context

One of the practical limitations encountered during testing was the context window.

A document can be relatively small as a PDF file but still contain a large amount of text.

For example:
```text
PDF file size ≠ amount of text presented to the model
```
A document that looks manageable based on its file size can still produce a large amount of extracted text.

What to Do

If AnythingLLM reports that the workspace or model context is too large:

Start with a smaller document.
Test the workflow with one paper at a time.
Avoid uploading a large collection before validating the setup.
Check the context and embedding configuration in AnythingLLM.
Consider whether the entire document collection is actually needed for the task.

A good first experiment is:
```text
1 research paper
        ↓
Validate retrieval
        ↓
Test analysis
        ↓
Add another paper
```

## 5. A Response Does Not Seem Grounded in the Paper

A technically convincing answer is not necessarily a correct answer.

If a response seems questionable:

Ask the assistant where the information comes from.
Locate the relevant section in the original paper.
Check the original text.
Compare the AI interpretation with the source.

A useful principle is:
```text
AI response
    ↓
Check retrieved information
    ↓
Check original document
    ↓
Validate
```
The Research Companion should accelerate research—not replace reading and technical judgement.

rather than uploading a large research library immediately.
