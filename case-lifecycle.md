# Case Lifecycle

```text
┌──────────────────────────┐
│  Movie Ticket Request    │
│  Submit booking details  │
└────────────┬─────────────┘
             ↓
┌──────────────────────────┐
│       Availability       │
│ Check seats + cost       │
└────────────┬─────────────┘
             ↓
┌──────────────────────────┐
│   Customer Confirmation  │
│ Review → Confirm/Cancel  │
└───────┬───────────┬──────┘
        │           │
     Cancel       Confirm
        │           ↓
        │    ┌────────────────────┐
        │    │ Booking Execution  │
        │    │ Route + allocate   │
        │    │ seats + Ticket ID  │
        │    └──────────┬─────────┘
        │               ↓
        │    ┌────────────────────┐
        │    │   Notification     │
        │    └──────────┬─────────┘
        ↓               ↓
              Resolved Case
```

## Routing Decision

```text
Show Type
   │
   ├── Premium ──> PremiumShowQueue
   │
   └── Other ────> StandardShowQueue
```
