# Continue.dev for Amivero Developers

## Overview
Continue.dev is an open-source AI coding assistant that integrates directly into VS Code, providing AI pair programming capabilities while maintaining security and compliance standards required for government projects.

Key benefits for Amivero developers:
- Works with our self-hosted Open WebUI LLM infrastructure
- Keeps sensitive code within our secure environment
- Provides context-aware code assistance and explanations
- Supports your workflow with minimal context-switching
- Allows scaling with new developers added 

## Quick Start
1. Install the Continue.dev extension for VS Code
2. Configure it to use our internal Open WebUI instance
3. Set up your project-specific settings

For detailed setup instructions, see [SETUP.md](./SETUP.md).

## Security Guidelines
- Continue.dev is approved for use with Amivero's internal LLM infrastructure
- Open WebUI is approved for specific use cases at ICE
- When working on government projects, ensure our self-hosted model configuration is approved for the agency you support
- Do not enable cloud-based models for sensitive or classified projects
- Review and follow our [Security Policy](./security-policy.md) for AI tools

## Getting Help
If you encounter issues during setup or usage:
- Check the [Troubleshooting](./SETUP.md#troubleshooting) section
- Submit an issue in the internal tracker: [AI Tools Issues](https://github.com/amivero/dev-resources/issues)

## Resources
- [Official Continue Documentation](https://continue.dev/docs)
- [Open WebUi and Continue Dev](https://docs.openwebui.com/tutorials/integrations/continue-dev)
- [Video Tutorials](https://intranet.amivero.com/ai-tools/tutorials)


## Future Enhancements
- Encrypt chat/completions endpoint in Kubernetes pod
