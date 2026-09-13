# Make Blueprint

This folder contains the public Make.com Blueprint for the AI Operations Inbox project.

The Blueprint committed to this repository is intentionally sanitized for public sharing. It must not contain real API keys, bot tokens, webhook URLs, private chat IDs, spreadsheet IDs, OAuth credentials, or personal connection identifiers.

## Import notes

After importing the Blueprint into Make, configure your own:

- Custom Webhook
- OpenAI connection
- Make Data Store
- Telegram Bot connection and Chat ID
- Gmail connection
- Google Sheets connection and spreadsheet

The repository also contains synthetic sample order data under `sample-data/orders.csv` so the lookup logic can be recreated without exposing a private spreadsheet.

The Blueprint is not expected to run immediately after import until these environment-specific connections are configured.
