# Model Output

## Model
Gemini 2.5 Pro

## Why this model
Chosen for SQL generation, structured reasoning over relational schemas and analytical reporting queries.

---

## Generated SQL Query

```sql
/*
  Report: Ledger Monthly Transaction Summary
  Requested by: Jennifer Parker
  Reference Date: 2026-04-24
  Reporting Window: 2025-10-01 to 2026-03-31 (6 full months)
*/

SELECT 
    TO_CHAR(DATE_TRUNC('month', created_at), 'YYYY-MM') AS month,
    category,
    COUNT(id) AS transaction_count,
    ROUND(SUM(amount_cents) / 100.0, 2) AS total_volume_brl
FROM 
    transactions
WHERE 
    status = 'completed'
    AND created_at >= DATE_TRUNC('month', '2026-04-24'::DATE) - INTERVAL '6 months'
    AND created_at < DATE_TRUNC('month', '2026-04-24'::DATE)
GROUP BY 
    DATE_TRUNC('month', created_at),
    category
ORDER BY 
    month ASC,
    category ASC;
```

---

## Query Logic Breakdown

- Date filtering uses the reference date to return the six full months before April 2026: from `2025-10-01` to before `2026-04-01`.
- The query filters only transactions with `status = 'completed'`.
- Currency conversion is done by dividing `amount_cents` by `100.0` and rounding to 2 decimal places.
- The output is formatted as `YYYY-MM`.
- Ordering is done by month and category.
