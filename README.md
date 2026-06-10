# Odysseus-project
# Local AI Agent Workspace — Odysseus + OpenLLaMA (Mac Setup)

A self-hosted, privacy-first AI workspace running entirely on local hardware with no cloud dependency. Built using [Odysseus](https://github.com/idosal/AgentLLM), an open-source agentic workspace, with [Ollama](https://ollama.com) as the local model backend and an OpenLLaMA lite model for inference.

---

## Why I Built This

Most AI tools send your data to external servers. In fields like healthcare and finance — where I work and am building toward — that's a real constraint. This project was about getting a fully functional agentic AI environment running locally: no API keys, no telemetry, no data leaving the machine.

---

## Stack

| Component | Tool |
|---|---|
| Workspace / Agent UI | Odysseus (open-source) |
| Model Backend | Ollama |
| Model | OpenLLaMA (lite/quantized variant) |
| OS | macOS |
| Interface | Local web UI (localhost) |

---

## Setup Overview

### Prerequisites

- macOS (Apple Silicon or Intel)
- [Ollama](https://ollama.com) installed
- [Git](https://git-scm.com) and Python 3.11+
- Node.js (if running Odysseus natively)

### 1. Install and start Ollama

```bash
# Download from https://ollama.com and install
# Then pull a lightweight model
ollama pull openhermes  # or whichever lite model you're using
ollama serve
```

Ollama listens on `http://localhost:11434` by default.

### 2. Clone and run Odysseus

```bash
git clone https://github.com/idosal/AgentLLM.git
cd AgentLLM
npm install
npm run dev
```

Open `http://localhost:3000` in your browser.

### 3. Connect Ollama as the model provider

In Odysseus settings:
- Set provider to **Ollama**
- Base URL: `http://localhost:11434/v1`
- Select your pulled model from the dropdown

### 4. Test a basic agent task

Start with a simple prompt like *"Summarize what you know about yourself and your capabilities"* before moving to agentic tasks. Once the model responds cleanly, try multi-step tasks like web research workflows or file summarization.

---

## What I Tested

- Basic chat and multi-turn conversation with a local model
- Autonomous agent task execution (multi-step planning and tool use)
- Zero-telemetry operation — confirmed no outbound API calls during inference
- Model performance tradeoffs between response quality and speed on local hardware

---

## Key Takeaway

Running a local agentic workspace is more accessible than it sounds. The main constraint is hardware — response speed depends on your RAM and whether you have Apple Silicon (which handles quantized models well via Metal GPU acceleration). For a lite model on a modern Mac, latency is usable for experimentation and development purposes.

This setup is particularly relevant for **regulated environments** (healthcare, finance, legal) where data sovereignty matters and cloud AI tools introduce compliance risk.

---

## Relevance to My Work

I work in healthcare administration at a skilled nursing facility. Privacy-first tooling isn't abstract for me — it's a daily operational reality. This project was partly technical exploration and partly a proof of concept for what local AI deployment could look like in a HIPAA-sensitive environment.

---

## Resources

- [Odysseus GitHub](https://github.com/idosal/AgentLLM)
- [Ollama](https://ollama.com)
- [OpenLLaMA](https://github.com/openlm-research/open_llama)
- [llmfit — hardware-aware model recommendations](https://github.com/Mozilla-Ocho/llamafile)

---

## Author

**Daniel Ibragimov**
[danny.ibragimov1@gmail.com](mailto:danny.ibragimov1@gmail.com) · [danielibrag.github.io](https://danielibrag.github.io) · [linkedin.com/in/daniel-ibragimov](https://linkedin.com/in/daniel-ibragimov)
