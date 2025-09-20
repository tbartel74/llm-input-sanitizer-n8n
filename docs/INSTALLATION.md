# Installation Guide

This guide will help you set up the LLM Input Sanitizer in your n8n environment.

## Prerequisites

- n8n installation (self-hosted or cloud)
- Basic familiarity with n8n workflow imports
- Understanding of LLM security concepts

## Quick Start

### 1. Import the Workflow

1. Download the workflow file: `workflows/current/sanitizer.json`
2. In your n8n instance, go to **Workflows → Import from file**
3. Select the downloaded JSON file
4. Click **Import**

### 2. Configure Settings

The workflow uses a centralized configuration system. Adjust these settings in
the **Enhanced Sanitizer Config** node:

```javascript
// Core security features
ENABLE_UNICODE_NORMALIZATION: true,
ENABLE_HOMOGLYPH_DETECTION: true,
ENABLE_TOKEN_FRAGMENTATION_DETECTION: true,

// Threat detection thresholds
CRITICAL_THRESHOLD: 70,
HIGH_THRESHOLD: 40,
MEDIUM_THRESHOLD: 20,

// Processing limits
MAX_INPUT_LENGTH: 10000,
MAX_PROCESSING_TIME: 5000,
```

### 3. Test the Installation

1. **Run Test Generator**: Execute the workflow to generate 50+ test cases
2. **Check Metrics**: Verify precision, recall, and F1-score in the output
3. **Manual Testing**: Try your own input examples

## Integration Examples

### Basic Integration

```javascript
// Input format
{
  "message": "user input text here",
  "chatInput": "user input text here"
}

// Output format
{
  "clearoutput": "sanitized text",
  "injectiondetected": true/false,
  "securitylevel": "LOW|MEDIUM|HIGH|CRITICAL",
  "securityscore": 0-100
}
```

### Advanced Integration

See `examples/integrations/` for complete integration examples with:

- **Groq LLama Guard**: `groq-llama-guard.json`
- **Groq Prompt Guard**: `groq-prompt-guard.json`

## Configuration Options

### Security Thresholds

| Threshold | Default | Description |
|-----------|---------|-------------|
| CRITICAL  | 70      | Block immediately |
| HIGH      | 40      | Flag for review |
| MEDIUM    | 20      | Log and monitor |

### Processing Limits

| Setting | Default | Description |
|---------|---------|-------------|
| MAX_INPUT_LENGTH | 10000 | Character limit |
| MAX_PROCESSING_TIME | 5000ms | Timeout |
| MAX_DECODE_ITERATIONS | 10 | Decode loop limit |

### Feature Toggles

| Feature | Default | Description |
|---------|---------|-------------|
| UNICODE_NORMALIZATION | true | NFKC normalization |
| HOMOGLYPH_DETECTION | true | Cyrillic/Greek detection |
| TOKEN_FRAGMENTATION | true | Spaced token detection |
| EMBEDDING_HOOKS | false | Heavy semantic analysis |

## Troubleshooting

### Common Issues

## High Processing Time

- Reduce `MAX_INPUT_LENGTH`
- Disable `EMBEDDING_HOOKS`
- Check input complexity

## False Positives

- Lower threshold values
- Review pattern configurations
- Check homoglyph mappings

## Memory Issues

- Limit concurrent executions
- Reduce test case count
- Optimize workflow settings

### Performance Tuning

For high-volume production use:

1. **Optimize Thresholds**: Start with higher values and tune down
2. **Limit Features**: Disable heavy detection for simple use cases
3. **Batch Processing**: Process multiple inputs together
4. **Caching**: Implement result caching for repeated inputs

## Monitoring

### Key Metrics

- **Processing Time**: Should be under 5 seconds
- **Detection Rate**: Monitor precision/recall balance
- **Error Rate**: Watch for configuration issues
- **Resource Usage**: CPU and memory consumption

### Logging

Enable audit logging in configuration:

```javascript
ENABLE_AUDIT_LOGGING: true,
INCLUDE_RAW_MATCHES: true,
LOG_AUDIT: true
```

## Security Considerations

- **Test Environment**: Always test in isolated environment first
- **Sensitive Data**: Never use real credentials in test cases
- **Access Control**: Restrict workflow modification permissions
- **Updates**: Keep workflow updated with latest threat definitions

## Support

- **Issues**: Report bugs via GitHub Issues
- **Documentation**: See `docs/technical/architecture.md`
- **Examples**: Check `examples/integrations/`
- **Contributing**: Read `CONTRIBUTING.md`
