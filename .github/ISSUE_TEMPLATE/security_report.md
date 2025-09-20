---
name: Security vulnerability
about: Report a security issue or bypass (use private reporting for critical issues)
title: '[SECURITY] '
labels: ['security']
assignees: ''
---

**⚠️ IMPORTANT:** For critical security vulnerabilities, please use
[private vulnerability reporting](https://github.com/username/llm-input-sanitizer-n8n/security/advisories/new)
instead of this public issue.

## Vulnerability type

- [ ] Prompt injection bypass
- [ ] Unicode obfuscation bypass
- [ ] Fragmentation bypass
- [ ] Comment injection bypass
- [ ] XSS detection bypass
- [ ] Performance/DoS issue
- [ ] Configuration vulnerability
- [ ] Other: ___________

## Severity assessment

- [ ] Critical - Complete bypass of all protections
- [ ] High - Bypass of major detection categories
- [ ] Medium - Bypass of specific patterns
- [ ] Low - Minor issue or edge case

**Vulnerability description**
A clear description of the security issue and how it bypasses the sanitizer.

**Proof of concept**
**Attack payload:**

```text
[Provide the input that bypasses detection]
```

**Current sanitizer output:**

```json
{
  "clearoutput": "what the sanitizer returns",
  "injectiondetected": false,
  "securitylevel": "LOW",
  "comment": "should have been blocked"
}
```

**Expected behavior:**
The sanitizer should have:

- [ ] Detected the injection attempt
- [ ] Flagged with HIGH/CRITICAL security level
- [ ] Applied appropriate sanitization
- [ ] Triggered specific detection labels

## Attack technique

Describe the technique used:

- Fragmentation method
- Encoding/obfuscation approach
- Unicode characters exploited
- Comment/delimiter strategy
- Other evasion technique

## Impact assessment

- Could this be used to compromise LLM systems?
- What type of malicious actions could result?
- Are there mitigating factors?

## Suggested fix

If you have ideas for how to address this:

- Pattern updates needed
- Detection logic improvements
- Configuration changes
- New validation rules

## Environment

- **Workflow version**: [e.g. v0.2]
- **Configuration**: [any custom settings that might affect detection]
- **Testing method**: [how you discovered this]

## Responsible disclosure

- [ ] I understand this issue will be publicly visible
- [ ] I have not disclosed this vulnerability elsewhere
- [ ] I am willing to work with maintainers on a fix
- [ ] I would like to be credited for the discovery (optional)
