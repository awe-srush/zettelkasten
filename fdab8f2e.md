---
date: 2020-07-24
---

# Secrets as a Secret

As a brief summary: I'd imagine that most people consider basic application security to be mostly solved by SaaS solutions like Vault and AWS Secrets Manager; they work well and implement most features people need.
However they either require vendor lock-in, or are prohibitively expensive to the point that I've been unable to get the budget (money and complexity) to use them.
Ergonomics are slowly improving, but I personally see a lot of issues even with the mainstream state of the art.

Whether or not someone would consider Secrets Management solved depends on how willing they are to settle with an inadequate solution, I feel.
Ultimately, despite the lack of satisfactory and ergonomic solutions out there, the pervasive culture of insecurity-by-default is so dominant that even implementing the barest amount of security is often sufficient to make you no longer a target.

For those who "need it", solutions like Vault work well if they can afford it, and if they can't, [AWS Secrets Manager](https://aws.amazon.com/secrets-manager/), or [blackbox](https://github.com/StackExchange/blackbox) do well as "good enough" solutions.
For the vast majority (in my experience), a `secrets.txt` stored on the Project Lead's laptop somewhere and pasted into an AWS config is what suffices.

## Are solutions like Hashicorp Vault or credstash working well?

[[4f7b2840]]

## Shortcomings

[[c787afbe]]

## What do you use, if anything?

[[ff78d7dc]]

## What would be a good solution for you?

[[904642dd]]
