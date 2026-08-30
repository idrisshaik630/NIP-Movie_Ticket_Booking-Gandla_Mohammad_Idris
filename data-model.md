# Data Model

## Movie Data Object

| Field | Purpose |
|---|---|
| Movie Name | Movie identifier/name |
| Genre | Movie category |

## Show Data Object

| Field | Purpose |
|---|---|
| Movie Name | Associated movie |
| Show Date | Screening date |
| Show Time | Screening time |
| Seat Capacity | Total seats |
| Show Type | Premium or Standard |
| Seat Availability Status | Availability result |
| Available Seats Count | Current available seats |
| Ticket Price | Price per ticket |

## Movie Ticket Request Case

| Field | Purpose |
|---|---|
| Customer Name | Customer identification |
| Movie Name | Selected movie |
| Show Date | Selected date |
| Show Time | Selected time |
| Show Type | Determines routing |
| Number of Tickets | Requested tickets |
| Seat Availability Status | Availability decision |
| Available Seats Count | Available capacity |
| Ticket Price | Unit price |
| Total Cost | Calculated price |
| Booking Status | Customer decision |
| Booking Confirmation Status | Booking result |
| Seat Numbers | Allocated seats |
| Ticket ID | Ticket reference |

## Relationship

```text
Movie
  │
  └── referenced by ──> Show
                         │
                         └── selected by ──> Movie Ticket Request
```

The supplied requirements specify reusable Movie and Show objects and their association with the Movie Ticket Request case.
