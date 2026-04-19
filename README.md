# ARIA – Local AI Assistant

> Fully local AI assistant built on Ollama, Open WebUI and Kokoro TTS.  
> No cloud. No data sharing. No subscription. Runs entirely on local hardware.

---

## Concept

ARIA (name inspired by the concept of a dedicated personal AI) is a locally 
hosted AI assistant configured to run completely offline on consumer hardware. 
The goal was to build a private, fast and customizable alternative to 
cloud-based AI services like ChatGPT – with full control over the model, 
behavior and data.

---

## Hardware Requirements

| Component | Minimum | Used in this build |
|---|---|---|
| CPU | 8 cores | AMD Ryzen 9 7950X3D |
| RAM | 32 GB | 64 GB DDR5 |
| GPU | 8 GB VRAM | NVIDIA RTX 4080 Super |
| Storage | 50 GB free | NVMe SSD |
| OS | Windows 10/11 or Linux | Windows 11 |

---

## Software Stack

| Component | Purpose |
|---|---|
| Ollama | Local LLM runtime – runs AI models without internet |
| Hermes3:70b | The actual AI model powering ARIA |
| Open WebUI | Web-based chat interface (like ChatGPT but local) |
| Kokoro TTS | Text-to-speech – ARIA speaks her responses |

---

## Setup Guide

### 1. Install Ollama
Download and install Ollama from https://ollama.com  
Pull the model: ollama pull hermes3:70b

### 2. Install Open WebUI
Follow the installation guide at https://github.com/open-webui/open-webui  
Connect Open WebUI to your local Ollama instance.

### 3. Configure the Modelfile
Create a custom Modelfile to define ARIA's personality and behavior:

FROM hermes3:70b
SYSTEM """
You are ARIA, a dedicated personal AI assistant.
You are direct, precise and professional.
You do not use filler phrases or unnecessary disclaimers.
"""

Apply the Modelfile:

ollama create aria -f Modelfile

### 4. Install Kokoro TTS
Follow setup instructions at https://github.com/remsky/Kokoro-FastAPI  
Configure Open WebUI to use Kokoro as the TTS engine.

---

## Known Limitations

- Hermes3:70b requires significant VRAM – 8B variant available for weaker hardware
  but system prompt compliance is unreliable on the 8B model
- Response speed depends heavily on GPU VRAM and CPU performance
- Windows reinstallation requires full setup from scratch – 
  consider documenting your exact configuration before any OS reset

---

## Status
> ⚠️ **Currently inactive** – setup requires reinstallation after OS reset

---

## Why Local AI?

- Complete privacy – no data ever leaves your machine
- No usage limits or subscription costs
- Full control over model behavior via Modelfile
- Works fully offline – field deployable
