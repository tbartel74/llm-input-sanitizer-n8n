
# Multilayer Input Sanitizer for Large Language Models (LLM) in n8n

This repository contains an **n8n workflow** (`n8n/workflows/sanitizer.workflow.json`) and supporting documentation (`docs/index.md`).
The workflow implements a **multi-layered input sanitization pipeline** to enhance the safety and robustness of interactions with Large Language Models (LLMs).

## 🚀 Quick Start

1. **Import the workflow** into n8n:
   Go to **Workflows → Import from file** and select `n8n/workflows/sanitizer.workflow.json`.
2. **Configure credentials & environment variables**
   Adjust any required settings (API keys, environment variables, etc.) before running.
3. **Run & monitor**
   Execute the workflow and observe logs to verify correct sanitization and behavior.

## ✨ Features

* **Normalization** – cleans input (trimming, Unicode normalization, removal of control characters).
* **Rule-based filters** – detects and blocks common attack patterns (e.g., prompt injection attempts).
* **Heuristics** – lightweight checks for suspicious or manipulative input.
* **Optional classifiers** – integration with toxicity/safety models.
* **PII handling** – redact or mask sensitive personal data before forwarding to the LLM.

---


## 📂 Repository Structure

```text
.
├── n8n/workflows/sanitizer.workflow.json  # Main workflow
├── docs/index.md                          # Project documentation
├── examples/                              # Usage examples (optional)
└── .github/workflows/ci.yml               # Basic CI: JSON + Markdown validation
```
---

## 📖 Documentation

Detailed usage and design notes can be found in [docs/index.md](docs/index.md).

## 🤝 Contributing

Contributions, ideas, and feedback are welcome!
Please open an issue or a pull request if you’d like to help improve this project.

## 📜 License
Released under the [MIT License](LICENSE).
