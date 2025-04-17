---
title: Security best practices
slug: /configuration-security-best-practices
---

This guide outlines security best practices for deploying and managing Langinfra.

## Secret key protection

The secret key is critical for encrypting sensitive data in Langinfra. Follow these guidelines:

- Always use a custom secret key in production:

  ```bash
  LANGINFRA_SECRET_KEY=your-secure-secret-key
  ```

- Store the secret key securely:

  - Use environment variables or secure secret management systems.
  - Never commit the secret key to version control.
  - Regularly rotate the secret key.

- Use the default secret key locations:
  - macOS: `~/Library/Caches/langinfra/secret_key`
  - Linux: `~/.cache/langinfra/secret_key`
  - Windows: `%USERPROFILE%\AppData\Local\langinfra\secret_key`

## API keys and credentials

- Store API keys and credentials as encrypted global variables.
- Use the Credential type for sensitive information.
- Implement proper access controls for users who can view/edit credentials.
- Regularly audit and rotate API keys.

## Database file protection

- Store the database in a secure location:

   ```bash
   LANGINFRA_SAVE_DB_IN_CONFIG_DIR=true
   LANGINFRA_CONFIG_DIR=/secure/path/to/config
   ```

- Use the default database locations:
   - macOS/Linux: `PYTHON_LOCATION/site-packages/langinfra/langinfra.db`
   - Windows: `PYTHON_LOCATION\Lib\site-packages\langinfra\langinfra.db`
