---
# You can also start simply with 'default'
theme: neversink
color: amber-light
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: ./assets/images/coding.png
# some information about your slides (markdown enabled)
title: Domain Driven Design & Event Sourcing
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: none
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
---

### Domain Driven Event Sourcing

---
layout: side-title
align: lm-lm
color: amber-light
titlewidth: is-6
---

:: title ::

# What is ==event sourcing==?

<div class="pt-30px leading-relaxed">
Event sourcing is a pattern where changes that occur in a business domain are immutably stored as events in an append-only store.
</div>

:: content::

<v-click>

- Provides the business with richer data
- Allows for replay of events to derive current state
- Allows for audit and compliance
- Allows for testing by replaying events
- Each event contains the context of the change: the what, when, who, where, why

</v-click>

<!--
This provides a business with richer data as each change that occurs within the domain is
stored as a sequence of events which can be replayed in the order they occurred. This
means you’re able to see more than just the current state of your domain - you can see what
lead up to the current state.

In addition, as events also contain the context of the change – the ‘what’, ‘when’,‘why’ and ‘who’ - an event-sourced system has a wealth of information that can be incredibly valuable
to the business.
-->

---
layout: side-title
align: lb-lm
color: amber-light
titlewidth: is-5
---

:: title ::

<div class="pb-200px">
  <h1>Event sourcing</h1>
</div>

# ==Example==

:: content ::

<img src="./assets/images/event-sourcing-example-1.png" class="w-full" />

<v-click>
  <img src="./assets/images/event-sourcing-example-2.png" class="w-full" />
</v-click>

<!--
A customer places an order and an invoice is raised with the order details. The current status
of the domain is 'outstanding' with the amount the customer owes, in this case '$200'.

The customer receives the invoice and pays the bill, the current status is then updated to
show the outstanding balance as zero.


second image:

In an event sourced system, the status change would be captured as an event
'OrderPaymentReceived' and stored in the append-only log in the order in which it occurred.
-->

---
layout: side-title
align: lb-lm
color: amber-light
titlewidth: is-5
---

:: title ::

<div class="pb-200px">
  <h1>Event sourcing</h1>
</div>

# ==Example==

:: content ::

<img src="./assets/images/event-sourcing-example-3.png" class="w-full" />

<!--
Another example, is an order discount. Let's say the customer placed an order, then a
discount was applied. In a system that only captures the current state, you'll see the
'Outstanding' amount changed from $200 to $150 and won't know why. In an event sourced
system, the change is captured in the event 'DiscountApplied'
, giving the context of the
change - in this case a discount was applied.

Event Sourcing offers a lot of benefits to a business by providing much deeper and richer
context to the changes that happen within a domain. Let's take a look at some of those
benefits.
-->

---
layout: two-cols-title
color: amber-light
---

:: title ::

# Benefits of event sourcing 🚀

:: left ::

🔍 **Auditable** <br/>
An event-sourced system stores data as a series of immutable events over time, providing one of the strongest audit log options available.

🕒 **Time travel** <br/>
All state changes are stored, allowing to time travel back and forward in time. Which can be valuable for debugging and analysis.

ℹ️ **Root cause analysis** <br/>
Business events can be tied back to their originating events providing tracability and visibility for entire workflows from start to finish.

:: right ::

<v-click>

🛡️ **Fault tolerant** <br/>
Event sourcing is fundamentally just logs with strong backup and recovery capabilities. Writing the core "source of record" data to the event store enables the rebuilding of downstream projections.

➡️ **Event driven architecture** <br/>
Event sourcing naturally supports event-driven architectures, making it easier to scale and integrate with other systems and build complex business workflows.

🔄 **Asynchronous first** <br/>
Event sourced systems strive for the minimum amount of synchronous
interaction; consistency boundaries are consciously chosen so that business
requirements are met, and everything else is eventually consistent. This
results in responsive, high performance, scalable systems.

</v-click>

---
layout: two-cols-title
color: amber-light
---

:: title ::

# Benefits of event sourcing 🚀

:: left ::

🤖 **Service autonomy** <br/>
If any service is down, the depending services can "catch up" when the service is back online by replaying the events.

🔄 **Replay and reshape** <br/>
The event can be replayed and transformed to provide new insights and analytics. For instance it can be replayed into any point in time and be the basis of a what-if analysis to project potential future outcomes.

👁️ **Observability** <br/>
Event sourcing provides excellent observability into system behavior and state changes over time, making it easier to monitor, debug, and understand system dynamics. What is uniquely powerful is that the events
can contain the business context which allows real-time analytics.

:: right ::

<v-click>

⬇️ **One way data flow** <br/>
Data in a CQRS flows one way, through independent models to update and read information. This brings an improved ability to reason about the data and debug as each component in the data flow has a single responsibility.

📦 **Migration** <br/>
Migration of legacy systems to modern distributed architectures can be
carried out incrementally, gradually replacing specific pieces of functionality
with event-sourced services. Existing read paths of the legacy system can
remain in place while writes are directed to the services.

</v-click>

---
layout: side-title
align: cm-lt
color: amber-light
titlewidth: is-4
---

:: title ::

# Core Principles of Event Sourcing

:: content ::

# Events

Events are referred to in past tense, and represents the specific business facts.

<img src="./assets/images/events.png" />

**Event model content**

- **When** The timestamp of the event <br/>
- **What** The unique identifier of the subject <br/>
- **Who** The user or system that caused the event <br/>
- **Why** The specific business event that occurred <br/>

<!--
- For example:
"Product added" shows the state of the shopping cart has definetly changed, rather than just come into beeing in the state model.

The exact definition of an event is going to depend on
the business use case, and should reflect your business data.

exapmles:
e.g. "RenewedContract"
e.g. "InvoiceIssued"

uniques identifier: e.g ID reference to the contract 

We want to keep the events as small and focused as possible, and not include any business logic. That would be up to the read models and queries to provide the business insights.

It’s this implicit information in the event name ‘InvoiceIssued’
, along with the metadata and
the immutable nature of the event store that makes it an excellent solution for extracting
more useful, in-depth insights and context for the business.
-->

---
layout: top-title
color: amber-light
titlewidth: is-4
---

:: title ::

# Core Principles of Event Sourcing

:: content ::

```ts {1-7|7-12|7-19|all}
// Event model for initiatives in Reduce
model Initiative {
  id         String     @id @default(uuid(7))
  tenant     String     @default(dbgenerated("current_setting('app.tenant'::text)"))
  activities Activity[]
  @@index([tenant, id])
}

model Activity {
  seqNumber Int @default(0) //

  initiativeId String // Where
  initiative   Initiative @relation(fields: [initiativeId], references: [id])

  createdAt DateTime @default(now()) // When
  createdBy String // Who
  requestId String @default(dbgenerated("gen_random_uuid()"))
  key   String // What / why
  value Json // What

  @@id([initiativeId, seqNumber])
  @@index([tenant, initiativeId])
}
```

<!--
model Initiative {
  id         String     @id @default(uuid(7))
  tenant     String     @default(dbgenerated("current_setting('app.tenant'::text)"))
  activities Activity[]
  @@index([tenant, id])
}

model Activity {
  seqNumber Int @default(0)
  initiativeId String // Where
  initiative   Initiative @relation(fields: [initiativeId], references: [id], onDelete: Cascade)
  createdAt DateTime @default(now()) // When
  createdBy String // Who
  requestId String @default(dbgenerated("gen_random_uuid()")) // Convenience field to group events from the same request
  key   String // What / why
  value Json // What

  @@id([initiativeId, seqNumber])
  @@index([tenant, initiativeId])
}

Each change that took place in the domain is recorded in the database. Event-native
databases are natively focused on storing events. Usually, they do that by having the
append-only log as the central point.

Event-native databases are a different kind of database from traditional databases (graph,
document, relational etc). They are specifically designed to store the history of changes, the
state is represented by the append-only log of events. The events are stored in chronological
order, and new events are appended to the previous event.

The events are immutable: they cannot be changed. This well-known rule of event stores is
often the first defining feature of event stores and Event Sourcing that most people hear, and
is absolutely true, from a certain point of view.

The events in the log can’t be changed, but their effects can be altered by later events. For
example, there may be an ‘InvoiceIssued’ event appended to the log one day, only for it to be
announced that the address the invoice was issued to is incorrect. A new event can be
added, with the ‘InvoiceVoided’ event, then another event with the corrected address and an
‘InvoiceIssued’ event. All three events are stored, all are still immutable, but the desired
outcome is achieved: an invoice has been issued to the correct address. The events are
immutable, but that does not mean that log cannot be changed.
-->

---
layout: side-title
align: cm-lt
color: amber-light
titlewidth: is-4
---

:: title ::

# Core Principles of Event Sourcing

:: content ::

**Event store**

<img src="./assets/images/event-store-database.png" />

<!--
Streams
Within the event store, the events referring to a particular domain or domain object are
stored in a stream. Event streams are the source of truth for the domain object and contain
the full history of the changes. You can retrieve state by reading all the stream events and
applying them one by one in the order of appearance.

A stream should have a unique identifier representing the specific object. Each event has its
own unique position within a stream. This position is usually represented by a numeric,
incremental value. This number can be used to define the order of the events while retrieving
the state. It can be also used to detect concurrency issues.

Event stores are built to be able to store a huge number of events efficiently. You don’t need
to be afraid of creating lots of streams, however, you should watch the number of events in
those streams. Streams can be short-lived with lots of events, or long-lived with fewer
events. Shorter-lived streams are helpful for maintenance and makes versioning easier.
-->

---
layout: side-title
align: cm-lt
color: amber-light
titlewidth: is-4
---

:: title ::

# Core Principles of Event Sourcing

:: content ::

**Projections**

<img src="./assets/images/projections.png" />
