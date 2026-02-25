# Thoughtworks Hugging Face Demo & Reachy Mini Integration

This repository contains a set of Jupyter Notebooks and instructions for running the Hugging Face Ecosystem demonstration, along with a full local Reachy Mini Conversation App that connects to OpenAI's Realtime voice API.

## Repository Contents

### 1. The Jupyter Notebooks
These notebooks are designed for a fast-paced, 5-minute demonstration of the Hugging Face capabilities:
- `01_datasets_tokenizers.ipynb`: Explores fast data loading, streaming, and Rust-backed tokenizers.
- `02_transformers_accelerate.ipynb`: Shows how to easily use state-of-the-art models with `pipeline` and handle hardware placement natively using `accelerate`.
- `03_kernels.ipynb`: Demonstrates how to dynamically load highly optimized C++ hardware extensions from the HF Hub (`huggingface-kernels`).
- `04_reachy_mini_lerobot.ipynb`: Connects to physical Reachy Mini hardware and demonstrates `lerobot` integration.
- `05_zero_to_cv_in_10_lines.ipynb`: A 10-line Computer Vision prototype using zero-shot object detection (`facebook/detr-resnet-50`).

### 2. The Reachy Mini Conversation App
We have integrated the official open-source `pollen-robotics/reachy_mini_conversation_app` into this environment, with several quality-of-life enhancements for running on a Mac safely and without requiring the physical robot hardware.

#### Prerequisites
1. **Python Virtual Environment**: We recommend using `uv` to install dependencies from `requirements.txt`.
2. **OpenAI API Key**: Required for the WebRTC real-time voice loop. Store this in a `.env` file as `OPENAI_API_KEY=YOUR_KEY` or input it directly into the Gradio UI.
3. **Hugging Face Token**: Required if you want to use local vision (e.g., `SmolVLM2`), so it can download the gated models. Export it to your environment or run `huggingface-cli login`.

#### Running the App
To start the Gradio UI, activate your environment and run the conversation app. Here are the important flags to know about:

- `--gradio`: Launches the beautiful web UI so you can interact with the agent from your browser (http://127.0.0.1:7860/).
- `--local-vision`: Downloads and runs `SmolVLM2` locally on your machine for the physical robot's vision, rather than sending camera frames to OpenAI.
- `--no-camera`: Disables the webcam feed and head-tracking. Useful if you run into `AVFoundation` security permission issues on macOS.
- `--standalone`: **(Crucial for testing)** Skips the physical hardware daemon initialization. It mocks the Reachy SDK, allowing you to run the Gradio interface, talk to the LLM, and test the vision tools entirely in software without owning the physical robot.

**Example: Run completely in software, using your webcam or uploaded images to talk to the AI:**
```bash
reachy-mini-conversation-app --gradio --local-vision --standalone
```

**Example: Run with the physical Reachy Mini connected via USB/Daemon:**
```bash
reachy-mini-conversation-app --gradio --local-vision
```
