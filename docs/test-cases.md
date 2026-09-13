# Test Cases

These are the main scenarios used to validate the workflow.

| Case | Example | Expected result |
|---|---|---|
| Duplicate request | Existing `request_id` | Stops before OpenAI |
| Finance | Duplicate charge / refund request | Finance notification + human review |
| Support | Login/access problem | Support route |
| Sales | Pricing or demo request | Sales route |
| Operations | Delivery/order change | Operations route |
| Critical | Fraud/security-style request | Department alert + manager escalation |
| Customer acknowledgement | Request with email | Gmail acknowledgement |
| Verified anomaly | Order with `transaction_count > 1` | Verified anomaly notification |
| Manual verification | Order with `transaction_count <= 1` | Manual verification notification |
| Unknown department | Unexpected model output | Fallback/Admin route |

## Example: duplicate charge

Input:

```json
{
  "request_id": "REQ-1025",
  "source": "website",
  "customer_name": "David Cohen",
  "email": "david@example.com",
  "subject": "Duplicate charge",
  "message": "I was charged twice for order 14256 and I want a refund.",
  "received_at": "2026-09-13T23:10:00+03:00"
}
```

Expected results:

- OpenAI extracts `department = finance` and `order_number = 14256`.
- Request is stored once.
- Finance route runs.
- Human review is required.
- Customer acknowledgement is sent.
- Order lookup finds `transaction_count = 2`.
- Verified payment anomaly route runs.
