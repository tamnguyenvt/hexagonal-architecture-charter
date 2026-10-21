# Changelog

## 0.1.2 — 2026-10-21

- A new `hexagonal-naming` guide names every part of a hexagon by its role: use cases after their port without `For` (`SigningIn`), services verb first with `Service` last, functions named for what they return only in domain models.
- Errors are faults: `DomainFault`, `ApplicationFault` and `AdapterFault`, each with a `message` and a `fix`, sent to clients as a `FaultDTO`. A fault is internal unless raised with `{ internal: false }`, and an internal one reaches a client only as a general "something went wrong" message.
- The `service/` layer is described as where logic that grows or is shared between use cases lives, so a use case stays light.
- An internal fault is logged before it is cooked: a `ForWritingLogs` port, `StderrLogs` and `InMemoryLogs` adapters, and `LogFaultService`, which every use case calls.
- `/init-hexagon` scaffolds all of it: the fault files, `FaultDTO` and `toFaultDTO()`, the log and `LogFaultService`, even with `--no-example`. The greeting example is renamed after the naming guide (`GreetingVisitors`, `greetingOf()`) and shows a fault the visitor may know and an internal one that only reaches the log.

## 0.1.1 — 2026-10-06

- Rebuilt with the latest `cw`.
- **Breaking:** needs a Cherry Works that names primitives by id alone; the skill is now `/init-hexagon`, its script `scaffold-hexagon`, and the corpora `why-<guide>`.

## 0.1.0 — 2026-10-02

- First release: `/skill-init-hexagon` sets up a hexagonal architecture in TypeScript or JavaScript.
