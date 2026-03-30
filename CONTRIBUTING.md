# Contributing to 000028-TagbasedPolicy

Thank you for your interest in contributing to AWS First Cloud Journey workshops! This document provides guidelines and instructions for contributing.

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Getting Started](#getting-started)
- [Pull Request Process](#pull-request-process)
- [Style Guidelines](#style-guidelines)
- [Community](#community)

## 🤝 Code of Conduct

### Our Pledge

We pledge to make participation in our project a harassment-free experience for everyone, regardless of:
- Age, body size, disability, ethnicity
- Gender identity and expression
- Level of experience, education
- Nationality, personal appearance, race, religion
- Sexual identity and orientation

### Our Standards

**Positive behavior includes:**
- Using welcoming and inclusive language
- Being respectful of differing viewpoints
- Gracefully accepting constructive criticism
- Focusing on what is best for the community
- Showing empathy towards other community members

**Unacceptable behavior includes:**
- Trolling, insulting/derogatory comments, personal or political attacks
- Public or private harassment
- Publishing others' private information without permission
- Other conduct which could reasonably be considered inappropriate

### Enforcement

Instances of abusive, harassing, or otherwise unacceptable behavior may be reported by contacting the project team at contact@awsfirstcloudjourney.com. All complaints will be reviewed and investigated.

## 🎯 How Can I Contribute?

### Reporting Bugs

Before creating bug reports, please check existing issues. When creating a bug report, include:

**Bug Report Template:**
```markdown
**Describe the bug**
A clear and concise description of what the bug is.

**To Reproduce**
Steps to reproduce the behavior:
1. Go to '...'
2. Click on '...'
3. Scroll down to '...'
4. See error

**Expected behavior**
What you expected to happen.

**Screenshots**
If applicable, add screenshots.

**Environment:**
 - OS: [e.g., macOS, Windows, Linux]
 - AWS CLI version: [e.g., 2.13.0]
 - Hugo version: [e.g., 0.119.0]

**Additional context**
Any other relevant information.
```

### Suggesting Enhancements

Enhancement suggestions are tracked as GitHub/GitLab issues. When creating an enhancement suggestion, include:

**Enhancement Template:**
```markdown
**Is your feature request related to a problem?**
A clear description of the problem.

**Describe the solution you'd like**
A clear description of what you want to happen.

**Describe alternatives you've considered**
Alternative solutions or features you've considered.

**Additional context**
Any other context or screenshots.
```

### Improving Documentation

Documentation improvements are always welcome:
- Fix typos or grammatical errors
- Clarify confusing sections
- Add missing information
- Improve code examples
- Translate content

### Contributing Code

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Make your changes**
4. **Test your changes**
5. **Commit your changes**
   ```bash
   git commit -m 'Add amazing feature'
   ```
6. **Push to the branch**
   ```bash
   git push origin feature/amazing-feature
   ```
7. **Open a Pull Request**

## 🚀 Getting Started

### Development Setup

1. **Clone the repository**
   ```bash
   git clone https://gitlab.com/awsfirstcloudjourney/000028-TagbasedPolicy.git
   cd 000028-TagbasedPolicy
   ```

2. **Install Hugo**
   ```bash
   # macOS
   brew install hugo

   # Ubuntu/Debian
   sudo apt-get install hugo

   # Windows
   choco install hugo
   ```

3. **Run locally**
   ```bash
   hugo server -D
   ```

4. **View in browser**
   Open http://localhost:1313

### Project Structure

```
.
├── content/           # Workshop content (Markdown files)
├── static/            # Static files (images, etc.)
├── themes/            # Hugo theme
├── config.toml        # Hugo configuration
├── README.md          # English documentation
├── README.vi.md       # Vietnamese documentation
├── LICENSE            # MIT License
├── CHANGELOG.md       # Version history
└── CONTRIBUTING.md    # This file
```

## 📝 Pull Request Process

### Before Submitting

1. **Check existing PRs** to avoid duplicates
2. **Test your changes** thoroughly
3. **Update documentation** if needed
4. **Follow style guidelines**
5. **Add/update tests** if applicable

### Pull Request Template

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix (non-breaking change fixing an issue)
- [ ] New feature (non-breaking change adding functionality)
- [ ] Breaking change (fix or feature causing existing functionality to change)
- [ ] Documentation update

## How Has This Been Tested?
Describe your testing process

## Checklist
- [ ] My code follows project style guidelines
- [ ] I have performed a self-review
- [ ] I have commented my code where necessary
- [ ] I have updated the documentation
- [ ] My changes generate no new warnings
- [ ] I have added tests that prove my fix/feature works
- [ ] New and existing tests pass locally
```

### Review Process

1. **Automated checks** must pass
2. **At least one maintainer** review required
3. **All comments** must be addressed
4. **Maintainer approval** before merge

## 🎨 Style Guidelines

### Markdown Style

- Use ATX-style headers (`#` prefix)
- One blank line before and after headers
- Use `**bold**` for emphasis
- Use `_italics_` for subtle emphasis
- Use fenced code blocks with language identifiers
- Keep lines under 120 characters when possible

### Code Style

#### Bash/Shell Scripts
```bash
#!/bin/bash
set -euo pipefail

# Use descriptive variable names
AWS_REGION="us-east-1"

# Add comments for complex logic
# This function deploys resources
deploy_resources() {
    local stack_name=$1
    aws cloudformation create-stack \
        --stack-name "$stack_name" \
        --template-body file://template.yaml
}
```

#### Python Scripts
```python
#!/usr/bin/env python3
# Module docstring describing purpose

def function_name(parameter: str) -> str:
    # Function docstring describing purpose
    # Args: parameter - Description of parameter
    # Returns: Description of return value

    # Implementation
    return result
```

#### CloudFormation/YAML
```yaml
AWSTemplateFormatVersion: '2010-09-09'
Description: Clear description of stack purpose

Parameters:
  ParameterName:
    Type: String
    Description: Parameter description
    Default: default-value

Resources:
  ResourceName:
    Type: AWS::Service::Resource
    Properties:
      PropertyName: Value
```

### Commit Message Guidelines

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation only
- `style`: Code style (formatting, missing semicolons, etc.)
- `refactor`: Code refactoring
- `test`: Adding tests
- `chore`: Maintenance tasks

**Examples:**
```
feat: add CloudFormation deployment option
fix: correct IAM policy permissions
docs: update README with new prerequisites
```

## 🌐 Translation Guidelines

### Adding Translations

1. Create new file: `README.<language-code>.md` (e.g., README.vi.md)
2. Translate all content accurately
3. Maintain same structure and formatting
4. Update links to point to translated versions
5. Add language badge to translated README

### Translation Checklist

- [ ] All headings translated
- [ ] All body text translated
- [ ] Code comments translated (if applicable)
- [ ] External links verified
- [ ] Internal links updated
- [ ] Images have alt text translated
- [ ] Badges updated with language indicator

## 👥 Community

### Communication Channels

- **GitLab Issues**: Bug reports and feature requests
- **GitLab Discussions**: General questions and discussions
- **Email**: contact@awsfirstcloudjourney.com
- **Website**: https://awsfirstcloudjourney.com

### Recognition

Contributors are recognized in:
- Repository contributors list
- Release notes
- Community acknowledgments

## 📜 License

By contributing, you agree that your contributions will be licensed under the MIT License.

## ❓ Questions?

Don't hesitate to ask questions:
- Open an issue with `question` label
- Email: contact@awsfirstcloudjourney.com
- Join community discussions

## 🙏 Thank You!

Your contributions make AWS First Cloud Journey workshops better for everyone. Thank you for being part of our community!

---

<p align="center">
  <i>Happy contributing! 🚀</i>
</p>
