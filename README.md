# CineWave Movie Ticket Booking Management

A **Pega Platform™** case-management application designed for CineWave Entertainment to manage movie ticket booking requests from submission through confirmation, ticket processing, notification, and SLA tracking.

> **Program:** National Internship Program (NIP) · Pega Academy · 2026  
> **Platform:** Pega Platform™

## Problem Statement

CineWave Entertainment currently handles movie ticket booking and tracking manually through emails and offline systems. This causes delays, limited visibility, and inefficient customer communication.

The application provides a structured digital workflow for:

- Customers to submit movie ticket requests
- Staff/booking agents to check show availability
- Automatic booking-cost calculation
- Customer confirmation or cancellation
- Reusable Movie and Show data
- Seat allocation and ticket generation
- Booking confirmation notifications
- SLA tracking
- Automatic routing based on show type

## Case Lifecycle

```text
Submit Request
      ↓
Check Availability + Calculate Cost
      ↓
Review & Confirm
   ↙        ↘
Cancel     Confirm
   ↓          ↓
Resolve   Booking Execution
              ↓
       Allocate Seats / Ticket ID
              ↓
       Send Confirmation
              ↓
           Resolve
```

## Main Case Type

**Movie Ticket Request**

The case represents the complete end-to-end movie booking process.

### Key Case Properties

| Property | Purpose |
|---|---|
| Customer Name | Identifies the customer |
| Movie Name | Requested movie |
| Show Date | Date of screening |
| Show Time | Screening time |
| Show Type | Premium or Standard |
| Number of Tickets | Requested quantity |
| Seat Availability Status | Availability result |
| Available Seats Count | Current available seats |
| Ticket Price | Price per ticket |
| Total Cost | Calculated booking amount |
| Booking Status | Confirmation/cancellation state |
| Booking Confirmation Status | Final booking state |
| Seat Numbers | Allocated seats |
| Ticket ID | Generated ticket reference |
| Case ID | Pega case reference |

## Reusable Data Objects

### Movie

- Movie Name
- Genre

### Show

- Movie Name
- Show Date
- Show Time
- Seat Capacity
- Show Type
- Seat Availability Status
- Available Seats Count
- Ticket Price

The Movie and Show objects are associated with the **Movie Ticket Request** case type so that movie and schedule information can be reused consistently.

## User Stories

| ID | Feature |
|---|---|
| US-001 | Submit Movie Ticket Request |
| US-002 | Check Show Availability |
| US-003 | Calculate Booking Cost |
| US-004 | Confirm Booking Request |
| US-005 | Maintain Movie and Show Data |
| US-006 | Review Booking Details |
| US-007 | Process Ticket Booking |
| US-008 | Notify Booking Confirmation |
| US-009 | Define Booking SLA |
| US-010 | Route Booking Request by Show Type |

## Business Rules

### Availability

Booking proceeds only when seats are available.

### Cost Calculation

```text
Total Cost = Ticket Price × Number of Tickets
```

The value should be calculated automatically and stored in the case.

### Confirmation

- **Confirmed** → continue to ticket processing
- **Cancelled** → resolve the request without further processing

### Queue Routing

```text
IF Show Type = Premium
    → PremiumShowQueue
ELSE
    → StandardShowQueue
```

A **When rule** or **Decision Table** can be used.

### SLA

- Goal: **1 day**
- Deadline: **2 days**
- Missed goal: flag the case as approaching deadline
- Missed deadline: automatically increase case priority

## Notification

After successful booking completion, the customer receives a confirmation containing:

- Case ID
- Movie Name
- Show Date & Time
- Number of Tickets
- Seat Numbers
- Total Cost

See [`docs/sample-correspondence.md`](docs/sample-correspondence.md).

## Pega Implementation Overview

1. Complete Pega environment setup and application creation.
2. Use Pega Blueprint to generate the initial application scaffold.
3. Create the **Movie Ticket Request** case type.
4. Configure stages and steps.
5. Create Movie and Show reusable data objects.
6. Add properties and validations.
7. Configure availability and cost-calculation logic.
8. Configure customer confirmation.
9. Configure booking execution and seat allocation.
10. Configure correspondence.
11. Configure the 1-day goal / 2-day deadline SLA.
12. Configure Premium/Standard queue routing.
13. Test the complete lifecycle.

## Suggested Repository Structure

```text
CineWave-Movie-Ticket-Booking-Management/
├── README.md
└── docs/
    ├── project-documentation.md
    ├── user-stories.md
    ├── data-model.md
    ├── case-lifecycle.md
    ├── business-rules.md
    ├── testing.md
    └── sample-correspondence.md
```

## Testing Checklist

- [ ] Customer can create a Movie Ticket Request
- [ ] Required booking fields are validated
- [ ] Movie and Show data can be reused
- [ ] Availability is checked before booking
- [ ] Booking is blocked when seats are unavailable
- [ ] Total Cost is calculated correctly
- [ ] Customer can confirm the request
- [ ] Customer can cancel the request
- [ ] Confirmed bookings reach Booking Execution
- [ ] Seat numbers are recorded
- [ ] Ticket ID is maintained
- [ ] Premium shows route to PremiumShowQueue
- [ ] Standard shows route to StandardShowQueue
- [ ] Confirmation correspondence is generated
- [ ] SLA goal and deadline behave correctly

## Expected Outcome

The application provides a consistent case-driven booking process with better visibility, automated decision-making, customer confirmation, ticket tracking, queue-based work assignment, notifications, and SLA management.

## Important Note

This repository contains the **project documentation and implementation blueprint** based on the supplied NIP/Pega Academy requirements. The actual Pega application rules, case types, data objects, queues, and configurations must be built and tested inside the student's Pega Academy instance.

## Source

Requirements are based on the supplied **Movie Ticket Booking Management Application** project brief from the National Internship Program (NIP) / Pega Academy, 2026.

---

## 📽️ Application Demo & Walkthrough

- **Project:** CineWave – Movie Ticket Booking Application
- **Developer:** Gandla Mohammad Idris
- **Platform:** Pega App Studio
- **Video Link:** [Watch Full Demo on YouTube](https://youtu.be/Q36GJDnkRlM?si=nu7oFyzDEyUCv2Uc)

### Key Stages Demonstrated:
1. **Event Setup:** Inputting movie title (*Pushpa*), date, showtime, and seat count.
2. **Availability & Pricing:** Verifying seat quota and automated price calculation ($40.00).
3. **Approval:** Review and confirmation by operator/manager.
4. **Booking Execution:** Automated seat allocation (*A12, A13*) and ticket generation.
5. **Correspondence:** Automated confirmation email dispatch.

---
