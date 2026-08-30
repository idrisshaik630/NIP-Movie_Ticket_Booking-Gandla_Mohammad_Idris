# Testing Plan

## Functional Test Cases

| Test | Expected Result |
|---|---|
| Submit complete booking request | Case is created |
| Submit request with missing required data | Validation prevents submission |
| Request available seats | Case continues |
| Request unavailable show | Booking does not proceed |
| Calculate cost | Total Cost = Ticket Price × Number of Tickets |
| Customer confirms | Case moves to booking execution |
| Customer cancels | Case resolves without booking |
| Premium show | Routed to PremiumShowQueue |
| Standard show | Routed to StandardShowQueue |
| Booking execution | Seats and Ticket ID are recorded |
| Successful booking | Confirmation correspondence is generated |
| Goal exceeded | Case is flagged |
| Deadline exceeded | Case priority increases |

## End-to-End Scenario

1. Customer creates Movie Ticket Request.
2. Customer selects movie/show details.
3. System/agent verifies availability.
4. System calculates total cost.
5. Customer reviews booking details.
6. Customer confirms.
7. Case is routed according to Show Type.
8. Seats are allocated.
9. Ticket ID is recorded.
10. Confirmation is generated.
11. Case is resolved.
