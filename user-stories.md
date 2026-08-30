# User Stories & Acceptance Criteria

## US-001 — Submit Movie Ticket Request

**Goal:** Customer initiates a booking.

**Requirements:**
- Case type: Movie Ticket Request
- Initial stage captures booking details.
- Capture Movie Name, Show Date, Show Time, Number of Tickets.
- Validate accuracy and completeness.
- Associate the case with Movie and Show data objects.

## US-002 — Check Show Availability

**Goal:** Verify seats before booking.

**Requirements:**
- Availability stage.
- Capture Seat Availability Status and Available Seats Count.
- Continue only when seats are available.

## US-003 — Calculate Booking Cost

**Goal:** Provide accurate pricing.

**Rule:**

`Total Cost = Ticket Price × Number of Tickets`

The value is calculated automatically and stored in the case.

## US-004 — Confirm Booking Request

**Goal:** Customer confirms or cancels.

**Requirements:**
- Approval stage.
- Customer makes the decision.
- Confirmed → ticket processing.
- Cancelled → resolve appropriately.

## US-005 — Maintain Movie and Show Data

**Goal:** Reuse movie/show information.

**Movie fields:**
- Movie Name
- Genre

**Show fields:**
- Movie Name
- Show Date
- Show Time
- Seat Capacity

These objects are associated with the booking case.

## US-006 — Review Booking Details

Before confirmation, display:
- Movie Name
- Show Timing
- Number of Tickets
- Total Cost

## US-007 — Process Ticket Booking

For confirmed bookings:
- Allocate seats.
- Update booking status.
- Store Booking Confirmation Status.
- Store Seat Numbers.
- Store Ticket ID.

## US-008 — Notify Booking Confirmation

After successful completion, send correspondence containing:
- Case ID
- Movie Name
- Show Date & Time
- Seat Numbers
- Total Cost

## US-009 — Define Booking SLA

Configure:
- Goal: 1 day
- Deadline: 2 days
- Missed goal → approaching-deadline flag
- Missed deadline → increased case priority

## US-010 — Route Booking Request by Show Type

If Show Type is Premium:

`PremiumShowQueue`

Otherwise:

`StandardShowQueue`

Use a When rule or Decision Table.
