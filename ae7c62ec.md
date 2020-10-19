---
date: 2020-08-06
---

# CI/CD Failure Strategies and Conditional Execution

These are actually the same thing.
[[cb92f30c]] contains some insight, however, it lacks insight on `retry` and other more advanced failure/conditional executions.
In a DAG, this is easy, it's just enriching the DAG into a CFG (by providing an explicit transition function).
