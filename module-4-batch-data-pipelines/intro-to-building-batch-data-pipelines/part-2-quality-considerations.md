# Why do we want to process data

## Purposes of Data Quality Processing

### Validity

- If data does not conform to our business rules, we have a problem of validity.
- For example, let's say that we sell movie tickets, and each ticket costs $10. If we have a $7 transaction, then we have a validity problem.

### Accuracy

- Happens due to data not conforming to objective truth.
- For example, mismatch with truth lookup table

### Completeness

- When we have a situation of failing to process everything
- For example, missing data

### Consistency

- If two different operations ought to be the same but yield different results
- For example, duplicate records

### Uniformity

- Data values of the same column in different rows mean different things
- For example, different units of measurement

## How to solve these problems?

- Use ELT and BigQuery with help of SQL and Views to address most of the problems

### BigQuery Example to Solve Consistency and Validity

- We can use BigQuery SQL count distinct function to remove duplicates.
- We can also define range when doing SQL query in order to ensure that the provided user view has only valid range data
