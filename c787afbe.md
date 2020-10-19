---
date: 2020-08-06
---

# Secret Management Engineering Concerns

- [How the secret is injected](https://www.netmeister.org/blog/passing-passwords.html)
- [Too many types of secrets needed, too few handled](https://dzone.com/articles/devops-and-the-proliferation-of-secrets)
- Difficulty of auditing secret usage
- Difficulty of rotating secrets
- Support of more advanced automatic security measures (such as [dynamic secrets](https://www.hashicorp.com/blog/why-we-need-dynamic-secrets/)).
- Despite [this Cryptographic RBAC paper coming out in 2013](https://eprint.iacr.org/2013/492.pdf), googling for cryptographic rbac solutions turns up no results, even in Hashicorp Vault.
- [Difficulty of defining, propagating, and enforcing Resource Based Access Control schemes](https://thenewstack.io/three-realistic-approaches-to-kubernetes-rbac/)
- How the [secret-zero problem](https://dzone.com/articles/how-to-eliminate-secret-zero-and-stop-nesting-secr) is handled. (Even [when handled](https://github.com/misurellig/hashitalks-demo), it's often error-prone and not as secure as it could be)

I'm sure I'm forgetting a few.
Social and bureaucratic factors also come into play in the real world, which further complicates matters.
