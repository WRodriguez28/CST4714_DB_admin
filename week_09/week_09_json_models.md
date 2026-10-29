{
  "users": [
    {
      "user_id": 103,
      "display_name": "Amina Yusuf"
    },
    {
      "user_id": 201,
      "display_name": "Priya Shah"
    }
  ],
  "tickets": [
    {
      "ticket_id": 1003,
      "subject": "Low water pressure",
      "status": "resolved",
      "requester_id": 103,
      "assignee_id": 201
    }
  ],
  "events": [
    {
      "event_id": 5005,
      "event_type": "created",
      "event_at": "2026-02-03 12:05:00+00"
    },
    {
      "event_id": 5006,
      "event_type": "status_changed",
      "event_at": "2026-02-03 14:25:00+00"
    },
    {
      "event_id": 5007,
      "event_type": "status_changed",
      "event_at": "2026-02-03 19:40:00+00"
    }
  ]
}

{
  "ticket_id": 1003,
  "subject": "Low water pressure",
  "status": "resolved",
  "requester_id": 103,
  "requester_name": "Amina Yusuf",
  "assignee_id": 201,
  "assignee_name": "Priya Shah",
  "events": [
    {
      "event_id": 5005,
      "event_type": "created",
      "event_at": "2026-02-03 12:05:00+00"
    },
    {
      "event_id": 5006,
      "event_type": "status_changed",
      "event_at": "2026-02-03 14:25:00+00"
    },
    {
      "event_id": 5007,
      "event_type": "status_changed",
      "event_at": "2026-02-03 19:40:00+00"
    }
  ]
}

In the referenced design from earlier, ticket 1003 in the tickets array was found by the application, finding also the requester’s name in the user’s array from using the requester_id. As well as to look up the event on the ticket in the ticket_events array. Each event that’s tied to a ticket should have an included ticket_id in order to connect to the ticket that it’s tied to. However, if there is any changes to the display name by the requested, then it should lead to only the user’s record to update. Within the hybrid/embedded design, the requester’s name and events directly inside the ticket object is founded by the application, but, changing the name of the requester would require an update to the embedded information, as well as the events array could possibly grow to a very large state as the years of history accumulate. This sort of a reference design keeps the information separated and easier to maintain, while the embedded design creates an easier way to retrieve information in one spot, but making the ticket document too big.

