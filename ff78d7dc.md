---
date: 2020-08-06
---

# KISS Secrets

Following the strategy of [[72196423]], I strive to start off with a secrets management solution that scales well without having any unnecessary overhead.

A few properties here help with that:

- A solution that has a lot of preexisting integration with other services helps a lot
- Likewise, try to find one that doesn't require the application or program to change its code when upgrading/modifying said solution

So, here's my strategy so far, based on the concept that environment variables have a ton of integration with every CI, code-hosting, dev environment, etc., platform out there.

---

The most important thing for me, when implementing a secrets management strategy, is developer ergonomics.
I will sacrifice a very large amount of security to make sure that the final solution is ergonomic enough to actually be used (correctly); given that the alternative is often worse than plain-text open secrets (being plain-text + false confidence that their "secrets" are "secure"), it's a compromise I find good enough for now.

What that usually ends up looking like:

- Have an `example.envrc` file that gives an example of secrets, and a `.envrc` file that's gitignored.
- In CI, inject variables using gitlab or github's mechanism for doing so.
  Use those to build the final application or product (if necessary) which is then deployed in a virtualized context (usually in containers) with the absolute minimum set of said secrets baked in.

The first upgrades I try to go for are: env variables -> secret files, encryption of secrets at rest (the `.envrc` file), and finally some secret management tool if I can.
I've only ever worked on one project that had enough motivation to progress to the point of using a secret management tool.
RBAC, secret-zero, secret rotation, auditing, and dynamic secrets have all been far too advanced and cost-ineffective.

It's always been cheaper to be hacked and compromised than spend the developer hours required to implement something more advanced than an encrypted env file.
