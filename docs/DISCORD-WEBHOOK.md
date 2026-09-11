# Discord Webhook

MacroCanvas can send workflow messages and completion notifications through Discord incoming webhooks.

## Supported uses

- Send a message from a workflow action.
- Report successful completion.
- Report a stopped or failed run.
- Include an error screenshot when that option is enabled.
- Expand placeholders such as workflow name, duration, row count, error, and machine name.

## Security

A Discord webhook URL contains a secret token.
Treat the entire URL as a credential.

- Never commit a real webhook URL.
- Never paste it into a public issue or shared example.
- Remove it before sharing a script.
- Revoke it in Discord if it is exposed.

MacroCanvas removes webhook values from its script-sharing export path.
You must configure the webhook again on the receiving installation.

## Delivery behavior

Discord may return HTTP `429` when requests arrive too quickly.
Respect the retry delay instead of sending repeated requests immediately.
Network errors, deleted webhooks, and Discord outages can prevent delivery without changing workflow execution results.

## Recommended test

1. Create a temporary private Discord channel.
2. Create a temporary incoming webhook.
3. Send a short test notification from MacroCanvas.
4. Confirm success and error templates separately.
5. Revoke the temporary webhook after testing.

[Back to English README](../README.md) · [Về README tiếng Việt](../README.vi.md)
