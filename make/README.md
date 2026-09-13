# Make Scenario

The automation is implemented in Make and the public portfolio blueprint is included as `scenario-blueprint.json`.

## Main modules

- Custom Webhook
- Make Data Store: duplicate check
- OpenAI: structured request classification
- JSON: Parse JSON
- Make Data Store: persist request
- Router + department filters
- Telegram notifications
- Human-review status update
- Gmail customer acknowledgement
- Google Sheets order lookup
- Payment-verification router

## Importing the public blueprint

The public blueprint is intentionally sanitized. Environment-specific identifiers were replaced or disconnected before publication.

After importing it into Make, reconnect or recreate:

- Custom Webhook
- OpenAI connection
- Make Data Store
- Telegram Bot connection and Chat ID
- Gmail connection
- Google Sheets connection and spreadsheet

The repository contains sample order data in `sample-data/orders.csv` so the lookup structure can be recreated without exposing a private spreadsheet.

## Security

No API keys, bot tokens, OAuth tokens, webhook URL, personal Telegram Chat ID, or private spreadsheet ID are included in the public blueprint.
