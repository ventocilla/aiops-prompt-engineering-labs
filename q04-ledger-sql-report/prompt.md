# Task
Generate a PostgreSQL SQL query for the Ledger monthly transaction report requested by Jennifer Parker.

The Ledger database has the following tables:

```sql
CREATE TABLE transactions (
  id              BIGSERIAL PRIMARY KEY,
  customer_id     BIGINT NOT NULL REFERENCES customers(id),
  category        VARCHAR(32) NOT NULL,
  amount_cents    BIGINT NOT NULL,
  status          VARCHAR(16) NOT NULL,
  payment_method  VARCHAR(16),
  created_at      TIMESTAMPTZ NOT NULL DEFAULT NOW(),
  completed_at    TIMESTAMPTZ
);

CREATE INDEX idx_transactions_created_at ON transactions(created_at);
CREATE INDEX idx_transactions_status ON transactions(status);
CREATE INDEX idx_transactions_category ON transactions(category);

CREATE TABLE customers (
  id          BIGSERIAL PRIMARY KEY,
  segment     VARCHAR(16) NOT NULL,
  country     CHAR(2) NOT NULL,
  signup_at   TIMESTAMPTZ NOT NULL DEFAULT NOW()
);
```

Production categories:
- subscription
- one_time
- refund
- credit_adjustment

Only transactions with `status = 'completed'` must be included.

The field `amount_cents` stores values in Brazilian cents and must be returned in BRL with 2 decimal places.

The reporting window is the last 6 full months from the reference date `2026-04-24`.

The output must be grouped by:
- month, formatted as `YYYY-MM`
- category

Each row must include:
- month
- category
- transaction count
- total volume in BRL

Final ordering:
- month ascending
- category ascending

# Action
Create the SQL query using PostgreSQL syntax.

The query must:
- use `date_trunc` or equivalent PostgreSQL date logic;
- filter only completed transactions;
- restrict the result to the last 6 full months based on `2026-04-24`;
- convert `amount_cents` to BRL using numeric division;
- round the total amount to 2 decimal places;
- group results by month and category;
- sort results by month and category;
- be readable and suitable for a production analytics/reporting context.

# Goal
The goal is to provide Jennifer Parker with a reliable monthly transaction report query that can be executed against Ledger without requiring her to write SQL.

The query must be accurate, readable and safe for reporting usage, preserving the expected business logic and date range.
