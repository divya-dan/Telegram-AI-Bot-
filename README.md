# Telegram AI Bot 🤖🧠

A lightweight Telegram bot that plugs an **open‑source large‑language model (LLM)** into your chats. Ask questions, brainstorm ideas, or just have fun—directly inside Telegram, with no external servers required.

> **Status :** Early “0.x” release—stable for personal use, but APIs & file layout may change.

---

## ✨ Key features

| Feature | What it gives you |
|---------|------------------|
| **Local LLM** (defaults to *GPT‑2*) | Runs entirely on your own machine—no OpenAI key needed. |
| **Easy setup** | `pip install -r requirements.txt`, add `.env`, run. |
| **Restart‑safe polling** | The bot cleans up previous instances to avoid duplicated replies. |
| **Slash‑commands** | `/help`, `/model`, `/temperature` with more coming. |
| **Typing indicator** | Shows *typing…* while the model generates, for better UX. |
| **Modular design** | Clear separation between Telegram logic and language‑model wrapper. |
| **MIT license** | Free for personal and commercial projects.

---

## 📸 Live demo

| ![demo GIF showing a user chatting with the bot](docs/demo.gif) |
|:--:|
| *The bot answering questions in a private chat* |

*(Record your own screen cast and drop the gif in `docs/demo.gif` to replace this placeholder.)*

---

## 🚀 Quick start

```bash
git clone https://github.com/divya-dan/Telegram-AI-Bot-.git
cd Telegram-AI-Bot-

# 1️⃣  Create a virtual environment (optional but recommended)
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts ctivate

# 2️⃣  Install dependencies
pip install -r requirements.txt

# 3️⃣  Configure your secrets
cp .env.example .env
# then edit .env and add your BOT_TOKEN from BotFather

# 4️⃣  Run the bot
python -m telegram_ai_bot   # or:  python scripts/run_bot.py
```

> **Need GPU?**  If `torch.cuda.is_available()` returns `True`, the model will automatically load to CUDA.

---

## ⚙️ Configuration

All runtime settings live in **environment variables** (loaded via [`python-dotenv`](https://github.com/theskumar/python-dotenv)).

| Variable | Required | Default | Purpose |
|----------|----------|---------|---------|
| `BOT_TOKEN` | ✅ | – | Token given by @BotFather. |
| `MODEL_NAME` |  | `gpt2` | Any HF model that supports causal text generation. |
| `MAX_LENGTH` |  | `200` | Maximum tokens in a single reply. |
| `TEMPERATURE` |  | `0.8` | Sampling temperature (0–2). |

Add more knobs in `telegram_ai_bot/config.py` and they will auto‑load.

---

## 🗂 Project layout

```
Telegram-AI-Bot-
├── telegram_ai_bot/           # Importable package
│   ├── __init__.py
│   ├── bot.py                 # Telegram handlers
│   ├── llm.py                 # Model wrapper
│   └── config.py              # Env‑var loader
├── scripts/
│   └── run_bot.py             # Thin entry‑point
├── tests/                     # pytest tests
├── requirements.txt
├── .env.example
└── README.md
```

See the [Architecture doc](docs/ARCHITECTURE.md) for design rationale.

---

## 🧪 Running tests

```bash
pip install -r requirements-dev.txt
pytest -q
```

All commits are linted & tested automatically via **GitHub Actions**.

---

## 🛣 Roadmap

- [ ] Slash command `/reset` to clear context
- [ ] Switch to **aiogram v3** (async) for scalability
- [ ] Docker image with tiny LLM baked‑in
- [ ] Streaming replies via *editMessageText*
- [ ] Model caching & dynamic model swap

Vote for features—or file your own—in the [issue tracker](https://github.com/divya-dan/Telegram-AI-Bot-/issues).

---

## 🤝 Contributing

PRs are welcome! Please:

1. Open an issue to discuss big changes first.
2. Follow the coding style enforced by **black**, **isort**, and **flake8**.
3. Add/adjust tests so CI stays green.

See [CONTRIBUTING.md](CONTRIBUTING.md) for full guidelines.

---

## 📄 License

This project is licensed under the **MIT License**—see [`LICENSE`](LICENSE) for details.

---

## 🙏 Acknowledgements

- [Hugging Face 🤗](https://huggingface.co/) for models & transformers library.
- [pyTelegramBotAPI](https://github.com/eternnoir/pyTelegramBotAPI) for Telegram integration.
- Every open‑source maintainer whose shoulders we stand on.

---

## ✍️ Citing this work

If this bot helps your research, please cite:

```text
@misc{telegram_ai_bot,
  title        = {Telegram AI Bot},
  author       = {Divyashree Doddbele Aswatha Narayana and Contributors},
  year         = {2025},
  howpublished = {\url{https://github.com/divya-dan/Telegram-AI-Bot-}}
}
```
