# Content

## Domain Driven Design

- 🗣️ **Ubiquitous Language**: A shared language between developers and domain experts
- 🔲 **Bounded Contexts**: Clear boundaries between different parts of your system
- 🎯 **Strategic Design**: Making architectural decisions based on business value
- 🧱 **Tactical Patterns**: Building blocks like Entities, Value Objects, and Aggregates

## Event Sourcing

- The state of your application is determined by a sequence of events
- All changes are captured as immutable events
- Events serve as both the system of record and audit log
- The current state can be rebuilt by replaying events

---

## Why Use Them Together?

DDD and Event Sourcing complement each other by:

- Capturing business behavior as meaningful events
- Providing a natural audit trail of system changes
- Enabling complex domain modeling
- Supporting eventual consistency in distributed systems
