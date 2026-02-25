# Weekend Challenge: Dive into the Hugging Face Universe! 🚀

Welcome to the Thoughtworks Weekend Challenge! Now that you've seen the power of the Hugging Face ecosystem and the Reachy Mini integration, it's your turn to get hands-on. 

This challenge is designed to take you from a complete beginner to running state-of-the-art AI models locally on your machine. All you need is a laptop and an internet connection. No physical robot required!

### Prerequisites
Before we begin, you need to set up your environment:
1. **Create a Free Hugging Face Account**: Head over to [huggingface.co/join](https://huggingface.co/join) to create your free profile.
2. **Generate an Access Token**: Go to your [settings/tokens](https://huggingface.co/settings/tokens) and generate a new token (Read access is fine). You'll need this to download certain models.
3. **Clone this Repository**: `git clone https://github.com/jomasego/hf_notebooks_reachy.git`
4. **Install Dependencies**: 
   ```bash
   cd hf_notebooks_reachy
   python -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```

---

## ⭐️ Challenge 1: Your First Multi-modal Prototype (Estimated time: 15 mins)
In the presentation, we showed how you can go from zero to a Computer Vision prototype in 10 lines of Python using the `transformers` library (`05_zero_to_cv_in_10_lines.ipynb`). 

**Your Task:**
1. Open the notebook: `jupyter notebook` and open `05_zero_to_cv_in_10_lines.ipynb`.
2. Find an image url online of a completely different scene (e.g., a bustling city street, a plate of food, or a sports game).
3. Replace the `url` variable in the notebook with your new image.
4. Run the notebook and inspect the object detection predictions.
5. **Bonus Points**: Change the model! The current model is `facebook/detr-resnet-50`. Go to the [Hugging Face Hub](https://huggingface.co/models?pipeline_tag=object-detection), filter by "Object Detection", find another model (like `yolos-tiny`), swap the `model="..."` string, and run it again. Compare the results!

---

## ⭐️⭐️ Challenge 2: Talk to the LLM via WebRTC (Estimated time: 20 mins)
The `reachy_mini_conversation_app` is a powerful open-source tool, but we modified it to run **standalone**, meaning you don't need the $10,000 robot to use it! It acts as an incredibly fast, low-latency, real-time voice assistant running right in your browser.

**Your Task:**
1. Install the Reachy Mini Conversation App dependencies (if you haven't already set up its specific virtual environment).
2. Get an OpenAI API Key (you will need this for the voice streaming loop).
3. Run the app in **Stand-alone** mode by passing the custom `--standalone` flag we added to bypass the hardware checks:
   ```bash
   reachy-mini-conversation-app --gradio --local-vision --standalone
   ```
4. Open your browser to `http://127.0.0.1:7860/`.
5. Enter your OpenAI API key in the side panel.
6. Click the orange **Record** button in the Stream panel and start talking! 

*Notice the almost zero latency response time! This is powered by the WebRTC integration.*

---

## ⭐️⭐️⭐️ Challenge 3: Local Vision Integration (Estimated time: 30 mins)
Let's combine everything. The Conversation App has a `--local-vision` flag. This tells the app *not* to use OpenAI to analyze images, but instead to download a powerful, small Vision-Language Model (`SmolVLM2-2.2B-Instruct`) from Hugging Face and run it natively on your Mac.

**Your Task:**
1. You must authenticate your terminal with Hugging Face so the app can download the gated `SmolVLM2` model. Run `huggingface-cli login` and paste the token you created earlier.
2. Start the app again with `--gradio --local-vision --standalone`.
3. Click **Record**.
4. Instead of just talking, hold something up to your webcam, or use the Gradio interface to upload an image into the chat.
5. Ask the voice assistant: *"What do you see in this image?"*

The system will now intercept your image, run inference locally on your own machine using the Hugging Face `SmolVLM2` model, and inject the description into the OpenAI conversation stream so the voice assistant can physically answer you about the image!

**Have fun, and welcome to the Hugging Face universe!**
