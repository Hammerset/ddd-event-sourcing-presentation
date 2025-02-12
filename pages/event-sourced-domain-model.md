# Event Sourced Domain Model

<!-- Page 110 - 113-->

## Advantages

- **Time traveling**: Domain events can construct not only the current state of the aggregate, but also any previous state.
  - Useful for debugging, auditing, and understanding how the system evolved over time
  - Debugging

- **Deep insights**: We can aggregate events into multiple aggregates - you can always add new projections that will leverage the events' data to provide additional insights.

- **Audit logs**: The domain events represents a strongly consistent audit log for the aggregates state.

- **Advanced optimistic concurrency management**: 


  <!-- - Debugging: It is possible to reconstruct past states to get the exact state of the system when a bug happened.

  - Possible to replay the events again to make sure the system is working as expected. 
  
  -->

