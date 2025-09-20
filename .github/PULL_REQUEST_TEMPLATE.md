# Pull Request

## Description
Brief description of the changes made and what problem they solve.

## Type of Change
- [ ] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [ ] Documentation update
- [ ] Performance improvement
- [ ] Security enhancement

## Changes Made
### Workflow Changes
- [ ] Modified detection patterns
- [ ] Updated configuration options
- [ ] Added new processing nodes
- [ ] Changed threshold values
- [ ] Other: ___________

### Documentation Changes
- [ ] Updated README
- [ ] Enhanced API documentation
- [ ] Added examples
- [ ] Updated installation guide
- [ ] Other: ___________

## Security Impact
### New Detections Added
- [ ] Prompt injection variants
- [ ] Unicode obfuscation techniques
- [ ] Fragmentation methods
- [ ] Comment injection styles
- [ ] Other attack vectors: ___________

### Detection Improvements
- [ ] Reduced false positives
- [ ] Improved accuracy
- [ ] Better performance
- [ ] Enhanced coverage
- [ ] Fixed bypass vulnerabilities

## Testing
- [ ] Imported workflow into n8n successfully
- [ ] Ran built-in test generator (50+ test cases)
- [ ] Tested with custom adversarial examples
- [ ] Verified backward compatibility
- [ ] Performance testing completed

### Test Results
**Before changes:**
- Precision: X.XX
- Recall: X.XX
- F1-Score: X.XX
- Processing time: XXXms avg

**After changes:**
- Precision: X.XX
- Recall: X.XX
- F1-Score: X.XX
- Processing time: XXXms avg

### New Test Cases
If you added new test cases, describe them:
- Attack vector covered: ___________
- Example input: ___________
- Expected detection: ___________

## Configuration Changes
- [ ] New configuration options added
- [ ] Default values changed
- [ ] Backward compatibility maintained
- [ ] Configuration documented

List any new configuration parameters:
```javascript
NEW_PARAMETER: default_value, // description
```

## Breaking Changes
- [ ] No breaking changes
- [ ] Configuration format changed
- [ ] Output format changed
- [ ] API changes made

If there are breaking changes, describe migration path:

## Workflow File
- [ ] Exported updated workflow as JSON
- [ ] Verified JSON syntax is valid
- [ ] Tested import in clean n8n instance
- [ ] File size is reasonable (< 1MB)

## Checklist
- [ ] My code follows the project's JavaScript style guidelines
- [ ] I have performed a self-review of my own changes
- [ ] I have commented complex logic appropriately
- [ ] My changes generate no new errors or warnings
- [ ] I have added/updated tests that prove my fix is effective
- [ ] New and existing tests pass with my changes
- [ ] I have updated documentation accordingly
- [ ] I have read and followed the [CONTRIBUTING.md](CONTRIBUTING.md) guidelines

## Additional Notes
Any additional information, concerns, or questions about this PR.

## Related Issues
Fixes #(issue number)
Closes #(issue number)
Relates to #(issue number)