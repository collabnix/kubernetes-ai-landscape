# Contributing to Kubernetes AI Landscape

Thank you for your interest in contributing to the Kubernetes AI Landscape! This project aims to provide a comprehensive and up-to-date collection of AI/ML tools, frameworks, and resources in the Kubernetes ecosystem.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How to Contribute](#how-to-contribute)
- [Adding New Tools](#adding-new-tools)
- [Updating Existing Information](#updating-existing-information)
- [Submission Guidelines](#submission-guidelines)
- [Review Process](#review-process)
- [Community](#community)

## Code of Conduct

This project adheres to the [Contributor Covenant Code of Conduct](https://www.contributor-covenant.org/version/2/0/code_of_conduct/). By participating, you are expected to uphold this code.

## How to Contribute

There are several ways to contribute to this project:

1. **Add new tools and frameworks**
2. **Update existing tool information**
3. **Improve documentation**
4. **Fix broken links**
5. **Suggest new categories**
6. **Share use cases and examples**

## Adding New Tools

### Criteria for Inclusion

Before adding a new tool, please ensure it meets the following criteria:

- **Kubernetes-native or Kubernetes-compatible**: The tool should work with or be designed for Kubernetes
- **AI/ML focused**: The tool should be specifically designed for AI/ML workloads or provide significant value to AI/ML practitioners
- **Open source or widely adopted**: Preference for open-source tools, but widely adopted commercial solutions are also welcome
- **Active maintenance**: The tool should be actively maintained with recent commits/releases
- **Production ready**: The tool should be suitable for production use or have a clear path to production readiness

### Information Required

For each new tool, please provide the following information:

| Field | Description | Required |
|-------|-------------|----------|
| Tool Name | Official name with link to homepage | ? |
| Description | Brief description (1-2 sentences) | ? |
| Category | Primary category (see existing categories) | ? |
| License | Software license (e.g., Apache 2.0, MIT) | ? |
| GitHub Stars | Current star count (for open source tools) | ? |
| Key Features | 3-5 main features or capabilities | ? |
| Supported Frameworks | ML frameworks supported (if applicable) | ? |
| Documentation Link | Link to official documentation | ? |
| Tutorial/Example | Link to getting started guide | ? |

**Legend**: ? Required, ? Optional but recommended

### Where to Add

Add new tools to the appropriate category table in the README.md file:

- **MLOps Platforms**: End-to-end ML platforms
- **Model Serving & Inference**: Tools for deploying models
- **Workflow Orchestration**: Pipeline and workflow management
- **Training & Experimentation**: Training frameworks and experiment tracking
- **Data Processing & Pipelines**: Data ingestion and processing
- **Monitoring & Observability**: Monitoring and logging tools
- **GPU & Resource Management**: GPU scheduling and resource optimization
- **Development & Notebooks**: Development environments
- **Security & Compliance**: Security and policy tools
- **Commercial & Managed Solutions**: Enterprise and cloud solutions

## Updating Existing Information

We encourage updates to keep information current and accurate:

- **GitHub Stars**: Update star counts quarterly
- **Version information**: Update to latest stable versions
- **License changes**: Track license changes
- **Feature updates**: Add new capabilities
- **Link updates**: Fix broken links or update to better resources

## Submission Guidelines

### Pull Request Process

1. **Fork the repository** to your GitHub account
2. **Create a feature branch** from main:
   ```bash
   git checkout -b feature/add-[tool-name]
   # or
   git checkout -b fix/update-[tool-name]
   ```
3. **Make your changes** following the format guidelines
4. **Test your changes** by checking:
   - All links work correctly
   - Markdown formatting is correct
   - Information is accurate and up-to-date
5. **Commit your changes** with a descriptive message:
   ```bash
   git commit -m "Add [Tool Name] to [Category] section"
   # or
   git commit -m "Update [Tool Name] information and links"
   ```
6. **Push to your fork**:
   ```bash
   git push origin feature/add-[tool-name]
   ```
7. **Create a Pull Request** with:
   - Clear title describing the change
   - Description explaining what was added/changed
   - Reference to any related issues

### Pull Request Template

When creating a pull request, please use this template:

```markdown
## Type of Change
- [ ] New tool addition
- [ ] Information update
- [ ] Documentation improvement
- [ ] Bug fix (broken link, typo, etc.)

## Description
Brief description of the changes made.

## Tool Information (if adding new tool)
- **Tool Name**: 
- **Category**: 
- **Homepage**: 
- **GitHub**: 
- **License**: 
- **Key Features**: 

## Checklist
- [ ] I have verified all links work correctly
- [ ] I have checked the tool meets inclusion criteria
- [ ] I have followed the formatting guidelines
- [ ] I have tested my changes locally
- [ ] I have read the contributing guidelines
```

### Formatting Guidelines

- Use proper Markdown syntax
- Maintain consistent table formatting
- Keep descriptions concise (1-2 sentences)
- Use title case for tool names
- Include proper links with descriptive text
- Sort tools alphabetically within each category

## Review Process

1. **Initial Review**: Maintainers will review for basic criteria and formatting
2. **Technical Review**: Subject matter experts will validate technical accuracy
3. **Community Feedback**: Community members may provide additional insights
4. **Final Approval**: Maintainers will merge approved contributions

### Review Criteria

- Accuracy of information
- Relevance to Kubernetes AI/ML ecosystem
- Quality of documentation links
- Consistency with existing format
- Value to the community

## Community

### Getting Help

If you need help with contributing:

- **GitHub Issues**: Create an issue for questions or suggestions
- **Slack**: Join our [Collabnix Community Slack](http://collabnix.com/slack)
- **Discussions**: Use GitHub Discussions for broader topics

### Recognition

Contributors will be recognized in several ways:

- Listed in the README acknowledgments
- GitHub contributor statistics
- Community shout-outs on social media
- Special recognition for significant contributions

## Style Guide

### Tool Descriptions

- Start with what the tool does
- Focus on key capabilities
- Avoid marketing language
- Keep it factual and neutral
- Maximum 150 characters

**Good**: "Open-source ML platform for Kubernetes with pipelines, notebooks, and model serving"

**Bad**: "Revolutionary AI platform that transforms your ML workflow with amazing features"

### Link Guidelines

- Use official websites as primary links
- Prefer documentation over marketing pages
- Check links are accessible and current
- Use HTTPS when available

### Table Formatting

- Maintain column alignment
- Use consistent capitalization
- Keep entries within reasonable length
- Sort alphabetically within categories

## Examples

### Adding a New Tool

```markdown
| [NewTool](https://newtool.io/) | Open-source model serving platform for Kubernetes | Model Serving | Apache 2.0 | 2.5k+ | Auto-scaling, Multi-framework, GPU support |
```

### Updating Tool Information

```markdown
# Before
| [ExistingTool](https://existing.io/) | ML platform | MLOps | MIT | 1k+ | Training, Serving |

# After  
| [ExistingTool](https://existing.io/) | Comprehensive ML platform for distributed training and serving | MLOps Platform | MIT | 1.5k+ | Distributed training, Model registry, Pipeline automation, Auto-scaling |
```

## Questions?

If you have any questions about contributing, please:

1. Check existing issues and discussions
2. Create a new issue with the "question" label
3. Join our community Slack for real-time help

Thank you for helping make the Kubernetes AI Landscape a valuable resource for the community!

---

**Happy Contributing!** ?

*This contributing guide is inspired by best practices from the open-source community and is continuously updated based on contributor feedback.*
