# Architecture

## Main scenario

The main Make scenario handles the request lifecycle from intake to routing and verification.

```text
Custom Webhook
  -> Duplicate Check
  -> OpenAI
  -> Parse JSON
  -> Make Data Store
  -> Main Router
```

### 1. Intake
A custom webhook receives a normalized request payload containing a request ID, source, customer details, subject, message and timestamp.

### 2. Idempotency
The request ID is checked against a Make Data Store before the OpenAI call. Existing IDs are stopped early so repeated deliveries do not create duplicate tickets or consume additional AI calls.

### 3. AI classification
OpenAI returns a strict structured object with the operational fields required by the workflow.

### 4. Persistence
The request is stored in a Make Data Store with a unique key based on `request_id`.

### 5. Business routing
A Make Router sends the request through one or more deterministic branches. A request can belong to Finance and, at the same time, trigger Human Review or Critical Escalation.

### 6. Order verification
When an order number is available, Make searches Google Sheets for the related order and evaluates transaction data using deterministic rules.

## Why the architecture is split this way

The model is responsible for language understanding. Make is responsible for operational decisions. This avoids giving the LLM direct authority over sensitive actions and makes the system easier to audit.
