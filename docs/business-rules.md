# Business Rules

## Department routing

Allowed departments:

- `finance`
- `support`
- `sales`
- `operations`

A fallback route handles unexpected values.

## Priority

Allowed priorities:

- `low`
- `medium`
- `high`
- `critical`

Critical requests trigger a separate manager escalation route.

## Human review

`requires_human = true` is used for cases where automation should not make the final decision, including refunds, suspicious payments, sensitive account or order changes, and ambiguous requests.

The request status is updated to `needs_review` in the Make Data Store.

## Duplicate prevention

The webhook `request_id` is used as the Data Store key. Existing IDs are blocked before the model call.

## Payment verification

The workflow does not treat the customer's claim as verified simply because the LLM classified it as a duplicate charge.

Order data is searched separately. The current demo rule is:

```text
transaction_count > 1 -> verified payment anomaly
transaction_count <= 1 -> manual verification
```

## Escalation

Manager escalation can be triggered by:

- `priority = critical`
- suspicious payment categories such as unauthorized charges

This rule is intentionally deterministic and does not depend only on the model's priority score.

## Customer communication

A Gmail acknowledgement confirms that the request was received and routed. It does not claim that a refund, cancellation, or other sensitive action has already been completed.
