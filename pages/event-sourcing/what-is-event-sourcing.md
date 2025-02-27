# What is Event Sourcing?

### The "better" / "rebel" way 
- ✅ Events is the source of truth
- ❌ State is the source of truth

### Events
- Factual statements about what happened

### State
- An interpretation of what happend

<!-- Presenter notes:
- Event Sourcing inverts the traditional approach to data storage
- Instead of storing current state, we store a sequence of events that led to that state
- Think of events like bank transactions vs. current balance
- Events are immutable facts - they represent what actually happened
- Benefits include: complete audit trail, ability to reconstruct past states, time-travel debugging 
- Great for business domains where history and transitions matter
-->

