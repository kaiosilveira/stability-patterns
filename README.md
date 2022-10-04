# Stability Patterns

When it comes to software engineering, production is a dangerous place for your newborn system to be in. As soon as you do the first release, your system becomes a possible victim of all kinds of failures, internal and external to it, and there is a good chance the all hell will in fact break loose, sometimes even multiple times in a single day. That's why in this series I'll be implementing, documenting and talking about some of the most common stability patterns, using Nygard's book "Release it!" as a standard reference.

## Stability patterns catalog

[Timeouts](https://github.com/kaiosilveira/nodejs-timeouts): Timeouts are a great way of avoiding slow responses and cascading failures, they help protecting our systems of hanging indefinitely while waiting for a response that might never come.

[Circuit breaker](https://github.com/kaiosilveira/nodejs-circuit-breaker): A circuit breaker in software engineering mimics the original mechanism used in electric engineering to protect circuits of burning down completely in case of failure. Circuit breaker protects your application of performing calls that would probably fail anyway by not executing them in the first place. It contains three states:

- `Closed`: Requests flow normally though
- `Open`: Requests do not flow through and operation is refused
- `Half-Open`: Next request is evaluated by the circuit breaker code, if it succeeds, the circuit state is changed to `Closed`, otherwise it goes back to `Open`.
