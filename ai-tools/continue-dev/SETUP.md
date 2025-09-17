# Continue.dev Setup Instructions for Amivero Developers

## Prerequisites
- VS Code (latest version recommended)
- Access to Amivero's internal network or VPN connection
- Credentials for Open WebUI (request from IT if you don't have these)

## Installation Steps

### 1. Install the Continue.dev Extension

#### Via VS Code Marketplace
1. Open VS Code
2. Click the Extensions icon in the Activity Bar (or press `Ctrl+Shift+X`)
3. Search for "Continue"
4. Locate "Continue" by Continue Dev (verify publisher)
5. Click "Install"

### 2. Configure for Amivero's Open WebUI

1. Follow the instructions here [Continue.dev VS Code Extension with Open WebUI](https://docs.openwebui.com/tutorials/integrations/continue-dev)
2. Below is a sample of how to setup the config.yaml

```
name: Local Agent
version: 1.0.0
schema: v1
models:
  - name: claude-7
    provider: openai
    model: us.anthropic.claude-3-7-sonnet-20250219-v1:0
    apiBase: https://amichat.dev.amivero-solutions.com/api
    apiKey: {{YOUR-API_KEY}}
    roles:
      - chat
      - edit

```


### 3. Verify Your Installation

1. Restart VS Code to ensure all settings are applied
2. Open a code file in your project
3. Press `Ctrl+Shift+/` (or your configured shortcut) to open Continue.dev
4. Type a test prompt like "Explain this code" to verify connectivity

## Government Project Configuration

When working on government projects:

1. Verify that only approved internal models are configured
2. For classified environments, confirm with your security officer that the configuration meets project requirements

## Troubleshooting

### Connection Issues
- **Symptom**: "Unable to connect to model"
  - **Fix**: Verify VPN connection is active
  - **Fix**: Check that your API key is correctly set


### Performance Issues
- **Symptom**: Slow responses or timeouts
  - **Fix**: Check if Open WebUI is under heavy load
  - **Fix**: Try switching to a lighter model in settings
  - **Fix**: Break complex queries into smaller, focused questions

### Extension Not Loading
- **Symptom**: Continue.dev sidebar doesn't appear
  - **Fix**: Check VS Code's extensions panel to verify Continue is installed
  - **Fix**: Run the "Developer: Reload Window" command
  - **Fix**: Check VS Code logs for extension loading errors