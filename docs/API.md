# API Documentation

This document describes the input/output interface and integration patterns for the LLM Input Sanitizer.

## Input Format

The sanitizer accepts various input formats automatically detected from the JSON payload:

### Standard Input

```json
{
  "message": "User input text to sanitize",
  "input": "Alternative input field",
  "text": "Another alternative field",
  "chatInput": "Chat-specific input field"
}
```

### With Configuration Override

```json
{
  "message": "User input text",
  "sanitizer_config": {
    "CRITICAL_THRESHOLD": 80,
    "MAX_INPUT_LENGTH": 5000,
    "ENABLE_UNICODE_NORMALIZATION": true
  }
}
```

## Output Format

The sanitizer returns a comprehensive JSON object with security analysis and sanitized content:

### Core Output Fields

```json
{
  "clearoutput": "Sanitized text safe for LLM consumption",
  "injectiondetected": true,
  "securitylevel": "CRITICAL",
  "securityscore": 85,
  "result": {
    "detected": true,
    "score": 85,
    "severity": "critical",
    "labels": ["fragmented_ignore", "reveal_terms"],
    "reason": "fragmented_ignore"
  }
}
```

### Detailed Analysis

```json
{
  "validation": {
    "originalInput": "Original input text",
    "length": 245,
    "isEmpty": false,
    "isSafe": false,
    "hasQuickThreats": true,
    "suspiciousUnicode": true
  },
  "normalization": {
    "normalized": "Normalized text",
    "changes": [
      {"from": "і", "to": "i"}
    ],
    "homoglyphsDetected": true
  },
  "fastDetection": {
    "score": 30,
    "matches": ["ignore", "system"]
  },
  "advancedDetection": {
    "matches": [
      {
        "pattern": "fragmented_ignore",
        "match": "i g n o r e",
        "weight": 40
      }
    ],
    "threatScore": 85
  }
}
```

### Audit Information

```json
{
  "details": {
    "audit": {
      "sanitization": [
        {
          "type": "placeholder_replacement",
          "original": "ignore previous instructions",
          "replacement": "[filtered:ignore_instructions]",
          "position": 45
        }
      ],
      "secretsMasked": [
        {
          "type": "api_key",
          "pattern": "Bearer token",
          "replacement": "[REDACTED]"
        }
      ]
    },
    "processingTime": 1250,
    "analysisVersion": "v0.2.0"
  }
}
```

## Security Levels

| Level | Score Range | Action Recommended |
|-------|-------------|-------------------|
| LOW | 0-19 | Allow with logging |
| MEDIUM | 20-39 | Allow with monitoring |
| HIGH | 40-69 | Review before allowing |
| CRITICAL | 70-100 | Block immediately |

## Detection Labels

### Prompt Injection
- `ignore_instructions` - "Ignore previous instructions" variants
- `reveal_system` - Attempts to reveal system prompts
- `role_manipulation` - "Act as system" style attacks
- `jailbreak_attempt` - DAN mode and similar bypasses

### Obfuscation Techniques
- `fragmented_tokens` - Spaced or dotted token splitting
- `zero_width_chars` - Invisible character insertion
- `homoglyph_substitution` - Cyrillic/Greek character substitution
- `unicode_obfuscation` - Complex Unicode manipulation

### Injection Methods
- `comment_injection` - Hidden in /* */ or // comments
- `delimiter_hiding` - Buried in --- or *** separators
- `template_syntax` - {{ }} or ${ } template patterns
- `xss_attempt` - JavaScript or HTML injection

### Data Leakage
- `secrets_exposure` - API keys, tokens detected
- `pii_present` - Personal information found
- `credential_attempt` - Password or auth data

## Integration Patterns

### Simple Gate Pattern

```javascript
// Check security level before LLM call
if (sanitizerOutput.securitylevel === "CRITICAL") {
  return { error: "Input blocked for security reasons" };
}

// Use sanitized output
const llmResponse = await callLLM(sanitizerOutput.clearoutput);
```

### Monitoring Pattern

```javascript
// Log all detections for monitoring
if (sanitizerOutput.injectiondetected) {
  logger.warn("Security detection", {
    score: sanitizerOutput.securityscore,
    labels: sanitizerOutput.result.labels,
    user: userId,
    timestamp: new Date()
  });
}
```

### Graduated Response Pattern

```javascript
switch (sanitizerOutput.securitylevel) {
  case "CRITICAL":
    return blockRequest();
  case "HIGH":
    return requireHumanReview();
  case "MEDIUM":
    return addWarningToResponse();
  case "LOW":
  default:
    return proceedNormally();
}
```

## Configuration API

### Runtime Configuration

Pass configuration overrides in the input:

```json
{
  "message": "user input",
  "sanitizer_config": {
    "CRITICAL_THRESHOLD": 60,
    "ENABLE_EMBEDDING_HOOKS": true,
    "MAX_PROCESSING_TIME": 10000
  }
}
```

### Available Configuration Options

#### Thresholds
```javascript
CRITICAL_THRESHOLD: 70,    // 0-100
HIGH_THRESHOLD: 40,        // 0-100
MEDIUM_THRESHOLD: 20,      // 0-100
```

#### Processing Limits
```javascript
MAX_INPUT_LENGTH: 10000,      // characters
MAX_PROCESSING_TIME: 5000,    // milliseconds
MAX_DECODE_ITERATIONS: 10,    // decode loops
```

#### Feature Toggles
```javascript
ENABLE_UNICODE_NORMALIZATION: true,
ENABLE_HOMOGLYPH_DETECTION: true,
ENABLE_TOKEN_FRAGMENTATION_DETECTION: true,
ENABLE_EMBEDDING_HOOKS: false,
ENABLE_LLM_GATEKEEPER_HOOKS: false,
```

#### Output Control
```javascript
STRICT_OUTPUT_MODE: true,      // strict validation
SANITIZE_LEVEL: 'maximum',     // maximum|standard|minimal
ENABLE_AUDIT_LOGGING: true,    // detailed logs
INCLUDE_RAW_MATCHES: true,     // include match details
```

## Error Handling

### Common Error Responses

```json
{
  "__error": "Input too long: exceeds MAX_INPUT_LENGTH",
  "errorType": "validation_error",
  "errorCode": "INPUT_TOO_LONG"
}
```

```json
{
  "__error": "Processing timeout: exceeded MAX_PROCESSING_TIME",
  "errorType": "timeout_error",
  "errorCode": "PROCESSING_TIMEOUT"
}
```

### Error Codes

| Code | Description | Resolution |
|------|-------------|------------|
| INPUT_TOO_LONG | Input exceeds length limit | Reduce input size or increase limit |
| PROCESSING_TIMEOUT | Analysis took too long | Simplify input or increase timeout |
| INVALID_CONFIG | Configuration error | Check config parameter format |
| UNICODE_ERROR | Unicode processing failed | Check input encoding |

## Performance Considerations

### Typical Processing Times

| Input Length | Processing Time | Memory Usage |
|--------------|----------------|--------------|
| < 1KB | 50-200ms | < 10MB |
| 1-10KB | 200-1000ms | 10-50MB |
| > 10KB | 1-5s | 50-200MB |

### Optimization Tips

1. **Disable Heavy Features**: Turn off embedding hooks for simple use cases
2. **Adjust Thresholds**: Higher thresholds = faster processing
3. **Limit Input Size**: Use MAX_INPUT_LENGTH appropriately
4. **Batch Processing**: Process multiple inputs together when possible

## Examples

See `examples/integrations/` directory for complete working examples:

- **Basic Usage**: Simple sanitization workflow
- **Groq Integration**: LLama Guard integration
- **Advanced Monitoring**: Full audit logging setup
- **Custom Configuration**: Tailored security settings