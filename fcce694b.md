---
date: 2020-07-24
---

# Test Suites

- 70:20:10 ratio
- 70% sub-1ms tests (no threading, no I/O)
- 20% medium tests (can TCP, I/O, etc)
- 10% large tests (full browser emulation, hardware running, etc).

- <https://danluu.com/everything-is-broken/>
  - ctrl+f `what's the best way to do it?`
- <https://danluu.com/testing/>
- <https://danluu.com/broken-builds/>
- <https://blog.patchgirl.io/haskell/2020/08/02/testing-haskell-with-stack-ghcid-and-hspec.html>
- <https://engineering.fb.com/2020/12/10/developer-tools/probabilistic-flakiness/> "automatically detecting how flaky a test is and checking for regressions in quality of tests".
  - We set out to find tests that don’t show any unreliable behavior (sometimes passing, sometimes not). We quickly realized that there aren’t any — all end-to-end tests have some degree of flakiness.
  - Every test framework and test environment brings an inherent level of flakiness that cannot be reduced by improving the test. PFS lets us compare the flakiness of a real-world test expressed in a particular test framework with the flakiness of the simplest possible test implemented using the same framework. When these two scores converge, it’s a sign that one cannot make the test any more reliable — unless one decides to improve the framework itself.
- <https://engineering.fb.com/2018/11/21/developer-tools/predictive-test-selection/>: <https://arxiv.org/abs/1810.05286>
  - Why using build dependencies is inefficient: Dependency tracking is not per function/feature/functionality granular
  - In practice, many transitive dependencies are not, in fact, relevant for regression testing.
  - To develop a better method, we consider a different question: What is the likelihood that a given test finds a regression with a particular code change?
  - To ensure that our test selection works well for real-world tests, the system needs to address the problem of test flakiness
    - When collecting training data, aggressively retry failed tests to make sure they're failing consistently and not just flaky
