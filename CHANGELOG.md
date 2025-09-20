# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- GitHub standard files (SECURITY.md, CONTRIBUTING.md, CODE_OF_CONDUCT.md)
- Enhanced .gitignore with comprehensive coverage

## [0.2.0] - 2024-09-XX

### Added

- Sequential sanitizer pipeline with 10-stage processing
- Enhanced test generator with 50+ adversarial examples
- Comprehensive threat scoring and classification system
- Advanced pattern detection with fragmentation tolerance
- Unicode normalization and homoglyph deobfuscation
- Comment injection and delimiter hiding detection
- Automated test result aggregation with metrics
- Configurable thresholds and processing limits
- Rich audit logging and transformation tracking

### Enhanced

- Multi-vector attack detection capabilities
- Zero-width character handling
- Template injection detection
- Secrets masking with pattern recognition
- Performance optimization with timeout controls

### Security

- Protection against fragmentation attacks
- Mitigation of Unicode-based obfuscation
- Detection of prompt injection attempts
- Prevention of XSS in LLM inputs
- Safeguards against data leakage

## [0.1.0] - 2024-09-XX

### Added

- Basic input sanitization workflow
- Initial prompt injection detection
- Simple pattern matching rules
- Basic test framework
- Documentation and examples

### Security

- Initial protection against common prompt injection
- Basic Unicode normalization
- Simple threat detection

## Types of Changes

- `Added` for new features
- `Changed` for changes in existing functionality
- `Deprecated` for soon-to-be removed features
- `Removed` for now removed features
- `Fixed` for any bug fixes
- `Security` for vulnerability fixes and security improvements
