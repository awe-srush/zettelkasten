---
date: 2020-07-31
---

# Weird Build Systems

- Dune
  - used arrows instead of monads. (simplifies static dependency approximation)
  - later redesigned to use selective functors
- Ninja: topological scheduler of make + verifying trace of shake
- Nix: course grained dependencies, precise hashing, downloading precomputed results
- pluto: shake + cyclic build rules w/user defined resolution strategy.
- tup: make but with refined dirty-bit implementation. Deletes stale results.
- redo: recursive build system. Very similar to shake.
- fabricate: build script that is traced at OS level to provide minimality.
  - cannot be encoded in Task method without switching from fetch callback to read + write callbacks.
  - shake's forward is a fabricate-like build system
  - stroll [^stroll] takes this to the logical conclusion by creating a build system from a list of shell commands
    - stroll also doesn't require tasks to be specified in the correct order.
    - stroll supports both dynamic outputs and dynamic inputs. Conjecture: these build systems cannot be minimal
- self adjusting computation:
  - can automatically adjust to an external change in inputs.
  - mostly used for in memory computations
  - support incremental processing of deltas
- memoizing: can be reduced to a minimal build system, but not vice versa. Minimal builds are a harder problem.
- functional reactive programming
  - Is the main difference between frp and a build system a push vs pull idea of being "notified" of changes?

[^stroll]: <https://blogs.ncl.ac.uk/andreymokhov/stroll/>
