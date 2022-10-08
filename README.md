🚧 **This repository is a work in progress and is being constantly updated. Check out the [#Roadmap](#roadmap) section below for details on what's planned for the near future** 🚧

# Stability Patterns

When it comes to software engineering, production is a dangerous place for your newborn system to be in. As soon as you do the first release, your system becomes a possible victim of all kinds of failures, internal and external to it, and there is a good chance that all hell will break loose, sometimes even multiple times in a single day. That's why in this series I'll be implementing, documenting and talking about some of the most common stability patterns, using Nygard's book "Release it!" as a standard reference.

## Technical details

All patterns are implemented with Typescript, using NodeJS and a thin layer of Express. Some sample projects for the patterns were forked from our public [nodejs-ts-express-template](https://github.com/unicornlauncher/nodejs-ts-express-template), which already implements some of the patterns being discussed, which is the case for the Handshaking Pattern, for instance. Unit tests were implemented using `jest` and the continuous integration pipeline is implemented using GitHub Actions.

## Roadmap

The roadmap for this project is publicly visible in the [Stability Patterns Roadmap](https://github.com/users/kaiosilveira/projects/4/views/1) project. Check it out if you're curious about what will be implemented in the near future and my ideas of examples.

## The stability patterns catalog

[Timeouts](https://github.com/kaiosilveira/nodejs-timeouts): Timeouts are a great way of avoiding slow responses and cascading failures, they help protect our systems from hanging indefinitely while waiting for a response that might never come.

[Fail fast](https://github.com/kaiosilveira/nodejs-fail-fast): Software systems eventually fail. They fail because of many reasons, but especially because of malformed inputs. In such cases, it's always better to _fail fast_, i.e., before compromising a lot of expensive resources in an optimistic attempt to execute an operation just to fail miserably later, making clients wait for much more time than they should.

[Handshaking](https://github.com/kaiosilveira/nodejs-handshaking): In **TCP**, to establish a connection, the client and the server should agree on the health of each other. This agreement is performed via a process called _handshake_. This pattern brings some perspective on how to mimic this approach when using HTTP.

[Circuit breaker](https://github.com/kaiosilveira/nodejs-circuit-breaker): A circuit breaker in software engineering mimics the original mechanism used in electric engineering to protect circuits from burning down completely in case of failure. Circuit breaker protects your application of performing calls that would probably fail anyway by not executing them in the first place. It contains three states:

- `CLOSED`: Requests flow normally through
- `OPEN`: Requests do not flow through and the operation is refused
- `HALF_OPEN`: Next request is evaluated by the circuit breaker code, if it succeeds, the circuit state is changed to `CLOSED`, otherwise, it goes back to `OPEN`
