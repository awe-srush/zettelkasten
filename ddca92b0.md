---
date: 2021-01-22
---

# Typed Configuration

<https://github.com/FlashSystems/just-config#no-data-types> makes an interesting argument that configuration shouldn't be typed.
I disagree with the conclusion but agree with the premise.
Me likey types, and I think you can get the best of both worlds.

To explain further: The example used is `cache_timeout=X`.
Should the value of X be constrained?
If you're validating a configuration file, you would constrain `X` to be a certain type.
If you're parsing a configuration file, you would not necessarily constrain `X`.

So, [Parse, don't validate](https://lexi-lambda.github.io/blog/2019/11/05/parse-don-t-validate/) strikes again.

Going back to the example, we have a situation here of mismatched concerns.

1. APIs should be [[c9983694]].
2. Configuration is also an API
3. Typing by validation is inherently not forwards/backwards compatible.

In the example, `X` is originally of type `Number`, then `Number | Disabled`, then `Number | Disabled` (but with support for parsing `Infinity` as a number).

So, the proper type of a configuration value is really `{key: string, value: bytestring}`.
This can be later parsed into a refined type when needed rather than validated at consumption.

Importantly... Parsing here does not prevent you from keeping the unparsed configuration around.

```
let cfg = getCfg() // Record<string, bytestring>

let cache_timeout = parseCacheTimeout(cfg)

fn parseCacheTimeout(cfg) {
  let timeout =
      // version 1
      try parseNum(cfg.?cache_timeout)
      `or`
      // version 2
      try parseString(cfg?.cache_timeout, "disabled")
      `or`
      // version 3
      try parseInfinity(cfg?.cache_timeout)
      // ... version N
      // forwards compat
      `or`
      configDefaultWithWarning(cfg, "cache_timeout")

  return timeout
}
```
