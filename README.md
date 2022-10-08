# Stability Patterns

When it comes to software engineering, production is a dangerous place for your newborn system to be in. As soon as you do the first release, your system becomes a possible victim of all kinds of failures, internal and external to it, and there is a good chance that all hell will break loose, sometimes even multiple times in a single day. That's why in this series I'll be implementing, documenting and talking about some of the most common stability patterns, using Nygard's book "Release it!" as a standard reference.

## Stability patterns catalog

[Timeouts](https://github.com/kaiosilveira/nodejs-timeouts): Timeouts are a great way of avoiding slow responses and cascading failures, they help protect our systems from hanging indefinitely while waiting for a response that might never come.

[Fail fast](https://github.com/kaiosilveira/nodejs-fail-fast): Software systems eventually fail. They fail because of many reasons, but especially because of malformed inputs. In such cases, it's always better to _fail fast_, i.e., before compromising a lot of expensive resources in an optimistic attempt to execute an operation just to fail miserably later, making clients wait for much more time than they should.

[Circuit breaker](https://github.com/kaiosilveira/nodejs-circuit-breaker): A circuit breaker in software engineering mimics the original mechanism used in electric engineering to protect circuits from burning down completely in case of failure. Circuit breaker protects your application of performing calls that would probably fail anyway by not executing them in the first place. It contains three states:

- `CLOSED`: Requests flow normally through
- `OPEN`: Requests do not flow through and the operation is refused
- `HALF_OPEN`: Next request is evaluated by the circuit breaker code, if it succeeds, the circuit state is changed to `CLOSED`, otherwise, it goes back to `OPEN`
