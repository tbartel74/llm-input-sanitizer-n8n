# Multilayer Input Sanitizer for Large Language Models (LLM) in n8n

This repository contains an **n8n workflow** implementing a **multi-layered input sanitization pipeline** to enhance the safety and robustness of interactions with Large Language Models (LLMs). The current workflow (`workflows/current/sanitizer.json`) provides comprehensive protection against prompt injection, Unicode obfuscation, and various attack vectors.

---

## 🚀 Quick Start

1. **Import the workflow** into n8n:
   Go to **Workflows → Import from file** and select
   `workflows/current/sanitizer.json`.
2. **Configure settings**
   Adjust thresholds and features in the **Enhanced Sanitizer Config** node
   based on your security requirements.
3. **Test & monitor**
   Run the built-in test generator to verify detection capabilities
   and monitor performance metrics.

For detailed setup instructions, see [docs/INSTALLATION.md](docs/INSTALLATION.md).

---

## ✨ Features

### 🔒 **Security Protections**
* **Prompt Injection Detection** – Identifies role manipulation and instruction bypass attempts
* **Unicode Attack Prevention** – Handles homoglyphs, zero-width chars, and fragmentation
* **Comment Injection Blocking** – Detects hidden payloads in /* */, //, # comments
* **XSS Protection** – Prevents JavaScript and HTML injection in LLM inputs
* **Secrets Masking** – Automatically redacts API keys, tokens, and credentials

### ⚡ **Advanced Detection**
* **Fragmentation-Tolerant Patterns** – Catches `i g n o r e` and `i.g.n.o.r.e` style attacks
* **Multi-Vector Analysis** – Combines multiple detection techniques for higher accuracy
* **Configurable Thresholds** – Adjustable security levels (LOW/MEDIUM/HIGH/CRITICAL)
* **Real-time Scoring** – Threat assessment with detailed audit logs

### 🧪 **Testing & Validation**
* **50+ Test Cases** – Built-in adversarial examples for validation
* **Performance Metrics** – Precision, recall, F1-score reporting
* **Automated Testing** – Regression testing with each workflow run

---

## 📂 Repository Structure

```text
.
├── .github/                    # GitHub configuration
│   ├── ISSUE_TEMPLATE/         # Issue templates
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── workflows/ci.yml        # CI/CD pipeline
├── docs/                       # Documentation
│   ├── API.md                  # API reference
│   ├── INSTALLATION.md         # Setup guide
│   └── technical/              # Technical documentation
├── examples/                   # Integration examples
│   └── integrations/           # Groq LLama/Prompt Guard examples
├── workflows/                  # n8n workflow files
│   ├── current/                # Latest sanitizer workflow
│   └── archived/               # Historical versions
├── CHANGELOG.md               # Version history
├── CONTRIBUTING.md            # Contribution guidelines
├── SECURITY.md               # Security policy
└── README.md
```

---

## 📖 Documentation

- **[Installation Guide](docs/INSTALLATION.md)** – Step-by-step setup instructions
- **[API Reference](docs/API.md)** – Input/output formats and integration patterns
- **[Technical Architecture](docs/technical/architecture.md)** – Detailed system design

## 🤝 Contributing

We welcome contributions! Please read our [Contributing Guidelines](CONTRIBUTING.md) and [Code of Conduct](CODE_OF_CONDUCT.md) before getting started.

### Quick Links
- **[Report Security Issues](SECURITY.md)** – Responsible disclosure process
- **[Submit Bug Reports](.github/ISSUE_TEMPLATE/bug_report.md)** – Help us improve
- **[Request Features](.github/ISSUE_TEMPLATE/feature_request.md)** – Suggest enhancements

---

## 📜 License

Released under the [MIT License](LICENSE).
