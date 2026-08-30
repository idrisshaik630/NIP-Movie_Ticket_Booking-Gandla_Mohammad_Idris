# Business Rules & Automation

## 1. Availability Rule

Booking may proceed only when the requested show has available seats.

## 2. Cost Rule

```text
Total Cost = Ticket Price × Number of Tickets
```

The calculated result should update automatically.

## 3. Confirmation Rule

```text
Booking Status = Confirmed
    → Booking Execution

Booking Status = Cancelled
    → Resolve Case
```

## 4. Queue Routing Rule

```text
IF Show Type = Premium
    THEN PremiumShowQueue
ELSE
    StandardShowQueue
```

A When rule or Decision Table can implement the decision.

## 5. SLA Rule

```text
Goal = 1 day
Deadline = 2 days
```

Missed goal:
- Flag case as approaching deadline.

Missed deadline:
- Increase case priority.

## 6. Notification Trigger

After successful booking completion, correspondence is generated for the customer with booking details.
