---
date: 2020-08-13
---

# Always Green Master

> The Not Rocket Science Rule Of Software Engineering:
> automatically maintain a repository of code that always passes all the tests

1. Open a PR
2. Approve a PR
3. Bot creates temp branch with PR rebased on top of master
4. Bot runs testsuite on temp branch
   - If it succeeds, it merges in
   - If it fails, it discards the branch
5. GOTO 1

## Bors / Marge bot

In general:

- You want one bot per project
- Bots automate "the workflow"
- Work with CI

- <https://github.com/bors-ng/bors-ng/issues/194#issuecomment-361011427>
  - Overview of different merging strategies
- bors (OG) was first: <https://github.com/graydon/bors>
  - Stateless
  - Polls CI for results. Only worked with buildbot + GitHub.
  - Runs as loop inside cron. Fires every minute.
- homu came next: <https://bors.tech/homu-io/>
  - <https://github.com/servo/homu>
  - used by rust and servo now
  - Stateful because of API rate limiting
  - Uses webhooks
  - Pushing instead of Polling: Test results from CI are pushed to Homu
- bors.tech is a rewrite of bors: <https://bors.tech/homu-io/>
  - Aims to be faster and more user friendly
  - Written in Elixir
- Marge bot: Bors for GitLab: <https://github.com/smarkets/marge-bot>
  - GitLab's api has a lot of limitations that make this bot error prone

---

references:

- <https://graydon2.dreamwidth.org/1597.html>
- <https://github.com/bors-ng/bors-ng>
- <https://buildbot2.rust-lang.org/homu/queue/rust>
- <https://about.gitlab.com/blog/2020/01/30/all-aboard-merge-trains/>
- <https://github.com/smarkets/marge-bot>
- <https://engineering.monday.com/?p=9714>
  - Interesting because it solves a [[d99dc068]] problem rather than a raw infrastructure problem.
  - Not the same as "merge trains" a la gitlab
