---
name: Bug report
about: Create a report to help us improve the sanitizer
title: '[BUG] '
labels: ['bug']
assignees: ''
---

**Describe the bug**
A clear and concise description of what the bug is.

**To Reproduce**

Steps to reproduce the behavior:

1. Import workflow '...'
2. Configure with '...'
3. Input text '...'
4. See error

**Expected behavior**
A clear and concise description of what you expected to happen.

**Actual behavior**
What actually happened, including error messages or unexpected output.

**Input and Output**

Please provide:

- **Input text**: The exact input that caused the issue
- **Expected output**: What the sanitizer should have detected/returned
- **Actual output**: What the sanitizer actually returned

```json
{
  "input": "your input text here",
  "expected": "what should happen",
  "actual": "what actually happened"
}
```

## Security Impact

- [ ] This is a security bypass (input that should be blocked but wasn't)
- [ ] This is a false positive (safe input that was incorrectly flagged)
- [ ] This is a performance issue
- [ ] This is a configuration issue
- [ ] Other: ___________

## Environment

- **n8n version**: [e.g. 1.0.0]
- **Workflow version**: [e.g. v0.2]
- **Platform**: [e.g. self-hosted, cloud]
- **Configuration changes**: [any custom threshold or settings]

**Additional context**
Add any other context about the problem here. Include screenshots if helpful.

## Test Results (if applicable)

If you ran the test generator, please include:

- Precision: X.XX
- Recall: X.XX
- F1-Score: X.XX
- Failed test IDs: [list any specific test cases that failed]
