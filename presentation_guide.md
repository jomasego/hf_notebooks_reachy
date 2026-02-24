# Hugging Face Capabilities: Thoughtworks Madrid
**Presentation Runbook & Speaker Guide**
**Target Duration:** < 5 Minutes

---

## 🛠 Preparation (To do *before* getting on stage)
1. **Connect the Hardware:** Ensure Reachy Mini is powered on and connected to your Mac/network.
2. **Setup Notebooks:** 
   - Open terminal: `cd /Users/jomasego/TW_HF_Demo`
   - Run: `source venv/bin/activate`
   - Run: `jupyter notebook`
   - Open `01`, `02`, `03`, `04`, and `05` notebooks in separate browser tabs and clear outputs (`Restart & Clear Output`).
3. **Setup Reachy Mini App & Daemon:**
   - Open a second terminal window: `cd /Users/jomasego/TW_HF_Demo`
   - Run: `source venv/bin/activate`
   - Start the hardware daemon: `reachy-mini-daemon`
   - Open a third terminal window: `cd /Users/jomasego/TW_HF_Demo/reachy_mini_conversation_app`
   - Run: `source .venv/bin/activate`
   - Ensure the `.env` has your `OPENAI_API_KEY`.
   - Run: `reachy-mini-conversation-app --gradio --local-vision`
   - Open `http://127.0.0.1:7860/` in a browser tab.
4. **Setup HF Space:**
   - Open `https://huggingface.co/spaces/jomasego/HF_TW_Demo` in a browser tab.

---

## ⏱ The 5-Minute Run-Through

### 0:00 - 0:30 | The Hugging Face Ecosystem
* **Visual:** Your introductory slide.
* **Talking Points:**
  - "Hugging Face is the best ally to anyone working with AI."
  - "Today, I'm going to rapidly demonstrate how the HF ecosystem allows you to go from raw data to a deployed API to advanced robotics in under 5 minutes."

### 0:30 - 1:30 | Fast Data & Tokenization (`01_datasets_tokenizers.ipynb`)
* **Action:** Switch to Notebook `01` tab. Run all cells.
* **Talking Points:**
  - "Everything starts with data. The `datasets` library gives us instant access to thousands of datasets from the Hub. Here we load the IMDB dataset."
  - *(Point to the Sentiment Distribution chart)* "We can instantly visualize our data distributions."
  - "Next, we use `tokenizers`. HF's Rust-backed tokenizers map over our entire dataset instantly."
  - *(Point to the lengths chart)* "And seamlessly plot the token lengths to prepare for model training."

### 1:30 - 2:30 | Inference & Acceleration (`02_transformers_accelerate.ipynb`)
* **Action:** Switch to Notebook `02` tab. Run all cells.
* **Talking Points:**
  - "With data ready, we use `transformers` to run state-of-the-art models in just 3 lines of code using `pipeline`."
  - "When we need more control, `accelerate` handles complex hardware logic for us. Notice `device_map='auto'` automatically optimally places the GPT-2 model on our Apple Silicon."
  - *(Point to the speed chart)* "Our generation loop takes just milliseconds natively on Mac MPS."

### 2:30 - 3:00 | Zero to CV in 10 Lines (`05_zero_to_cv_in_10_lines.ipynb`)
* **Action:** Switch to Notebook `05` tab. Run the cells.
* **Talking Points:**
  - *"We talk a lot about LLMs, but HF is a multi-modal universe. Whether you're working on Fraud Detection—like we are at Kleinanzeigen—or Audio processing, there is a pre-trained model waiting for you. You can go from zero to a working Computer Vision prototype in 10 lines of Python."*
  - *(Point to the object detection output)*: "Here we just ran state-of-the-art vision inference natively."

### 3:00 - 3:30 | Hugging Face Kernels (`03_kernels.ipynb`)
* **Action:** Switch to Notebook `03` tab. Run all cells.
* **Talking Points:**
  - "For those pushing boundaries on CUDA, `huggingface-kernels` allows you to dynamically load heavily optimized C++ hardware extensions directly from the HF Hub."
  - "There is no local compiling required. You pull down a FlashAttention or Quantization kernel just like you pull down a model."

### 3:30 - 4:15 | Scaling to Production (`jomasego/HF_TW_Demo` Space)
* **Action:** Switch to HF Space browser tab. Type a prompt and hit "Generate".
* **Talking Points:**
  - "When a local script is ready, deploying is instant with Hugging Face Spaces."
  - "This Gradio app runs on ZeroGPU hardware. The `@spaces.GPU` decorator tells HF to dynamically assign a GPU to the function exactly when a user clicks generate, scaling automatically from 0 to thousands of users without wasting idle GPU costs."

### 4:15 - 5:00 | Robotics at the Edge (Reachy Mini App)
* **Action:** Switch to Reachy Mini App tab (`http://127.0.0.1:7860/`).
* **Talking Points:**
  - "But HF isn't just for cloud APIs. We are powering physical edge AI robotics."
  - "This is the actual Reachy Mini Conversation App running locally on this Mac, connecting to the robot right here."
  - "Thanks to Hugging Face integrations, the app is downloading and executing `SmolVLM2` using my HF Pro account locally to process vision."
  - *(Interact with Reachy Mini)*: "Hey Reachy, look at the audience at Thoughtworks Madrid and tell me what you see!" or trigger a dance using the UI.
  - "From datasets, to prototypes, to cloud scaling, to physical edge robotics, Hugging Face provides the tools to build it all. Thank you."

---

## 💡 Pro-Tips for Success:
- Keep the pace fast! If a model takes a second to load, keep talking through what it's doing behind the scenes.
- Test the Reachy Mini conversation loop *before* the presentation audio environment changes (rooms full of people can mess with STT thresholds).
- Have your `.env` configured properly to ensure no hiccup during the live demo.
