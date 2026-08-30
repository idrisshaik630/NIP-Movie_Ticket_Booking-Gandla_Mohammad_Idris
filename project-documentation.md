# Project Documentation

## 1. Project Title

**CineWave Movie Ticket Booking Management Application**

## 2. Project Context

CineWave Entertainment needs to replace manual movie-ticket booking and tracking through emails and offline systems with a structured Pega Platform case-management application.

## 3. Objectives

The application is intended to:

1. Design an end-to-end booking case lifecycle.
2. Provide customer-facing booking interactions.
3. Model reusable Movie and Show data.
4. Automate availability and pricing decisions.
5. Capture customer confirmation.
6. Process seat allocation and ticket generation.
7. Notify customers after successful booking.
8. Apply booking SLAs.
9. Route work automatically according to show type.

## 4. Personas

### Customer
Submits booking details, reviews the booking, and confirms or cancels it.

### Booking Agent / Staff
Verifies show availability and performs booking-related operational work.

### System
Performs calculations, routing, status updates, SLA handling, and correspondence triggers.

## 5. Case Lifecycle

### Stage 1 — Request Submission

Capture:

- Movie Name
- Show Date
- Show Time
- Number of Tickets

Validate required information before submission.

### Stage 2 — Availability

Verify:

- Seat Availability Status
- Available Seats Count

The booking should proceed only when seats are available.

Calculate:

**Total Cost = Ticket Price × Number of Tickets**

### Stage 3 — Approval / Confirmation

Display:

- Movie Name
- Show Timing
- Number of Tickets
- Total Cost

Capture the customer's Booking Status.

### Stage 4 — Booking Execution

For confirmed requests:

- Allocate seats
- Update booking status
- Store seat numbers
- Generate/store Ticket ID
- Complete booking

Route the case to the correct queue using Show Type.

### Stage 5 — Resolution / Notification

After successful completion, send confirmation correspondence to the customer and resolve the case.

## 6. SLA

The booking case uses:

- Goal: 1 day
- Deadline: 2 days

When the goal is missed, the case should be flagged as approaching its deadline. When the deadline is missed, case priority should automatically increase.

## 7. Queue Routing

Premium or special screenings:

`PremiumShowQueue`

All other shows:

`StandardShowQueue`

The routing must happen automatically.

## 8. Acceptance Criteria

A booking is considered successfully implemented when a customer can submit a request, availability is verified, cost is calculated, booking details are reviewed, the customer confirms, seats/ticket information is recorded, the case is routed correctly, and a confirmation notification is generated.
