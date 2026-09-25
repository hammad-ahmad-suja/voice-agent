# 🎙️ LiveKit Voice AI Agent

A real-time AI voice assistant built with **LiveKit Agents**, **AssemblyAI**, **Google Gemma**, **Fish Audio**, and **AI Coustics**.

The agent can listen to a user's voice, process the conversation using an LLM, and respond naturally using text-to-speech. It also includes audio enhancement for improved voice input quality.

## ✨ Features

* 🎤 Real-time voice interaction
* 🧠 Google Gemma LLM for intelligent responses
* 🗣️ AssemblyAI Universal-3-5-Pro for speech-to-text
* 🔊 Fish Audio S2.1 Pro for text-to-speech
* 🎧 AI Coustics audio enhancement
* 🔄 STT-based turn detection
* 🌐 LiveKit real-time communication
* ⚡ Async Python implementation
* 🔐 Environment variable support with `python-dotenv`
* 🐍 Python 3.13 support

## 🛠️ Tech Stack

| Technology     | Purpose                                   |
| -------------- | ----------------------------------------- |
| Python         | Programming language                      |
| LiveKit Agents | Real-time voice agent framework           |
| AssemblyAI     | Speech-to-text                            |
| Google Gemma   | Large language model                      |
| Fish Audio     | Text-to-speech                            |
| AI Coustics    | Audio enhancement                         |
| uv             | Python package and environment management |
| python-dotenv  | Environment variable management           |

## 📁 Project Structure

```text
hammad-ahmad-suja-voice-agent/
│
├── README.md
├── agent.py
├── pyproject.toml
├── .python-version
│
└── src/
    └── voice_agent/
        └── __init__.py
```

## ⚙️ Requirements

Before running the project, make sure you have:

* Python 3.13
* uv
* A LiveKit Cloud/project setup
* Required API credentials
* Internet connection

## 🚀 Installation

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/hammad-ahmad-suja-voice-agent.git
cd hammad-ahmad-suja-voice-agent
```

### 2. Create the virtual environment

Using `uv`:

```bash
uv sync
```

This will install the dependencies defined in `pyproject.toml` and create the project environment.

### 3. Configure environment variables

Create a `.env` file in the project root:

```env
LIVEKIT_URL=your_livekit_url
LIVEKIT_API_KEY=your_livekit_api_key
LIVEKIT_API_SECRET=your_livekit_api_secret
```

Add any additional API credentials required by the inference providers you are using.

**Never commit your `.env` file or API keys to GitHub.**

You can create a `.gitignore` file containing:

```gitignore
.env
.venv/
__pycache__/
*.pyc
```

## ▶️ Run the Agent

Start the LiveKit agent with:

```bash
uv run python agent.py console
```

The agent can also be started using the configured project environment.

## 🎙️ How It Works

The voice pipeline follows this general flow:

```text
User Voice
    │
    ▼
LiveKit Room
    │
    ▼
AI Coustics Audio Enhancement
    │
    ▼
AssemblyAI Speech-to-Text
    │
    ▼
Google Gemma LLM
    │
    ▼
Fish Audio Text-to-Speech
    │
    ▼
Voice Response
    │
    ▼
User
```

### Speech-to-Text

The agent uses AssemblyAI's Universal-3-5-Pro model:

```python
stt=inference.STT(
    model="assemblyai/universal-3-5-pro",
    language="en",
)
```

This converts the user's spoken input into text.

### Language Model

Google Gemma is used to generate the assistant's responses:

```python
llm=inference.LLM(
    model="google/gemma-4-31b-it",
)
```

### Text-to-Speech

Fish Audio S2.1 Pro converts the generated response back into speech:

```python
tts=inference.TTS(
    model="fishaudio/s2.1-pro",
    voice="fa4c9eb3dccc4806b382b40d61c6b10a",
)
```

### Turn Detection

The project uses STT-based turn detection:

```python
turn_handling=TurnHandlingOptions(
    turn_detection="stt",
)
```

The project intentionally does not use `inference.TurnDetector()`.

### Audio Enhancement

AI Coustics is used to improve incoming audio:

```python
noise_cancellation=ai_coustics.audio_enhancement(
    model=ai_coustics.EnhancerModel.QUAIL_VF_S
)
```

This helps provide cleaner audio input for the voice pipeline.

## 🤖 Assistant Behavior

The assistant is configured to be:

* Helpful
* Friendly
* Concise
* Informative
* Curious
* Conversational
* Light-hearted

The assistant is also instructed to avoid complex formatting, emojis, asterisks, and unnecessary symbols in its spoken responses.

## 📦 Dependencies

The main dependencies include:

```text
livekit-agents==1.6.0
livekit-local-inference==0.2.5
livekit-plugins-ai-coustics==0.3.2
python-dotenv>=1.2.3
httpx>=0.28.1
```

They are automatically installed when running:

```bash
uv sync
```

## 🔧 Configuration

The project uses:

```text
.python-version
```

to specify:

```text
3.13
```

The Python package configuration is managed through:

```text
pyproject.toml
```

## 🧪 Development

To run the project in development mode:

```bash
uv run python agent.py console
```

If you modify the dependencies in `pyproject.toml`, run:

```bash
uv sync
```

again.

## 🔐 Security

Do not upload sensitive credentials to GitHub.

Make sure the following files are ignored:

```gitignore
.env
.venv/
__pycache__/
*.pyc
```

If an API key is accidentally committed, revoke it immediately and generate a new one.

## 🗺️ Future Improvements

Possible improvements for this project include:

* 🌍 Multi-language voice support
* 🧠 Conversation memory
* 🎤 Improved voice activity detection
* 👤 User authentication
* 📊 Conversation logging
* 🔊 Custom voice selection
* 🌐 Web-based frontend
* 📱 Mobile voice interface
* 🛠️ Custom tools and function calling
* 📈 Agent monitoring and analytics

## 👨‍💻 Author

**Hammad Ahmad Suja**

GitHub: `@hammad-ahmad-suja`

## 📄 License

This project is intended for educational and development purposes. Add your preferred open-source license here, such as MIT, if you want to distribute the project under an open-source license.

---

⭐ If you find this project useful, consider giving it a star on GitHub.
