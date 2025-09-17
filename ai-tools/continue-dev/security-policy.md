# Security Policy for AI Tools at Amivero

## Overview

When using Continue.dev and other AI coding assistants at Amivero, adherence to these security guidelines is mandatory, particularly for government projects.

## Data Protection Guidelines

### Never Share with AI Tools
- Classified information (at any level)
- PII or PHI data
- Customer proprietary information
- Access credentials or secrets
- Security implementation details

## Tool-Specific Security Controls

### Continue.dev Security Configuration
- Always use our internal Open WebUI infrastructure via the provided configuration
- Turn off Allow Anonymous Telemetry

## Compliance Requirements

### FedRAMP Projects
For projects requiring FedRAMP compliance:
- Only use Continue.dev with the approved internal model configurations
- Maintain logs of AI assistant usage if required by project security plan
- Report any security concerns or potential data exposures immediately

### Classified Environments
In classified environments:
- Verify with your security officer that Continue.dev is approved
- Use only in air-gapped environments with locally hosted model

## Incident Response

If you suspect sensitive information has been exposed to an AI model:
1. Disconnect from the AI service immediately
2. Report the incident to security@amivero.com
3. Document the nature of potentially exposed information
4. Do not discuss details over unclassified channels