# Security Policy

## Supported Versions

We actively maintain and provide security updates for the following versions:

| Version | Supported          |
| ------- | ------------------ |
| v0.2.x  | :white_check_mark: |
| v0.1.x  | :x:                |

## Reporting a Vulnerability

We take the security of our LLM input sanitizer seriously. If you discover a security vulnerability, please follow these steps:

### How to Report

1. **Do not** create a public GitHub issue for security vulnerabilities
2. Use GitHub's [private vulnerability reporting](https://github.com/username/llm-input-sanitizer-n8n/security/advisories/new) feature
3. Alternatively, email us at [your-email@domain.com] with details

### What to Include

Please include as much information as possible:

- Description of the vulnerability
- Steps to reproduce the issue
- Potential impact assessment
- Any suggested fixes or mitigation strategies
- n8n workflow version affected

### Response Timeline

- **Acknowledgment**: Within 48 hours
- **Initial Assessment**: Within 5 business days
- **Resolution**: Varies based on complexity, but we aim for 30 days maximum

### Security Measures

Our sanitizer is designed to protect against:
- Prompt injection attacks
- Unicode-based obfuscation
- Comment injection techniques
- Fragmentation attacks
- XSS attempts in LLM inputs
- Data leakage through PII exposure

We regularly test these protections and welcome responsible disclosure of any bypasses or new attack vectors.