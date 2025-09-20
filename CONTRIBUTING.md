# Contributing to LLM Input Sanitizer

Thank you for your interest in contributing to our LLM input sanitization project! This guide will help you get started.

## How to Contribute

### Reporting Issues

1. Check existing [issues](https://github.com/username/llm-input-sanitizer-n8n/issues) first
2. Use our issue templates for bug reports or feature requests
3. Provide detailed information about your n8n environment and workflow version

### Submitting Changes

1. **Fork** the repository
2. **Import** the workflow into your n8n instance
3. **Test** your changes thoroughly with the included test cases
4. **Export** the updated workflow as JSON
5. **Create** a pull request with clear description

### Development Workflow

#### Prerequisites
- n8n installation (self-hosted or cloud)
- Basic understanding of n8n workflow development
- Knowledge of security best practices for LLMs

#### Testing Your Changes

1. Import `n8n/workflows/v0.2/Sequential_Sanitizer_v0.2.json` into n8n
2. Run the built-in test generator (generates 50+ test cases)
3. Verify all detection metrics (precision, recall, F1-score)
4. Test with your own adversarial examples
5. Ensure performance remains within acceptable limits

#### Code Quality Standards

- **Workflow Structure**: Maintain the 10-node sequential pipeline architecture
- **Configuration**: Use the Enhanced Sanitizer Config node for all settings
- **Documentation**: Update inline comments in JavaScript code nodes
- **Testing**: Add new test cases for any new attack vectors you address
- **Performance**: Ensure processing time stays under configured limits

## Types of Contributions

### 🐛 Bug Fixes
- Security bypasses in detection logic
- Performance issues
- Configuration problems
- Documentation errors

### ✨ New Features
- Additional attack vector detection
- New sanitization techniques
- Integration examples
- Performance optimizations

### 📖 Documentation
- Setup instructions
- Usage examples
- Architecture explanations
- Best practices guides

### 🧪 Testing
- New adversarial test cases
- Edge case scenarios
- Performance benchmarks
- Integration testing

## Submitting Pull Requests

### PR Requirements

1. **Clear title** describing the change
2. **Detailed description** explaining the problem and solution
3. **Test results** showing improved detection metrics
4. **Updated documentation** if applicable
5. **Workflow JSON export** with your changes

### PR Template

```markdown
## Description
Brief description of changes made

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Performance improvement

## Testing
- [ ] Imported workflow into n8n
- [ ] Ran test generator (50+ cases)
- [ ] Verified detection metrics
- [ ] Tested with custom examples

## Metrics (if applicable)
- Precision: X.XX
- Recall: X.XX
- F1-Score: X.XX
- Processing time: XXXms average
```

## Security Considerations

Since this project deals with security:

- **Never** include real sensitive data in examples
- **Always** test against known attack vectors
- **Document** any new threats your changes address
- **Consider** performance impact of new detections
- **Validate** that changes don't break existing protections

## Code Style

### JavaScript in n8n Code Nodes

- Use clear, descriptive variable names
- Add inline comments for complex logic
- Follow existing code structure patterns
- Handle errors gracefully with try-catch blocks
- Maintain consistent formatting

### Configuration
- Use the centralized config system
- Avoid hardcoded values
- Document all new configuration options
- Provide sensible defaults

## Getting Help

- **GitHub Issues**: For bug reports and feature requests
- **Discussions**: For questions and general discussion
- **Documentation**: Check `docs/` folder for technical details

## Recognition

Contributors will be recognized in:
- Repository contributors list
- Release notes for significant contributions
- Special mentions for security improvements

Thank you for helping make LLM interactions safer! 🔒