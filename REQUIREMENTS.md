# Requirements

## Required Requirement Inputs

- Project purpose: A cooking event website, or events with a price per person and dishes that meet guest needs.
- Primary users / actors: Admin, Organizer, Attendee. The cook and grocery shopper receive order updates. Their user roles are UNKNOWN.
- Core workflows: Create events; set a price per person; select dishes; specify an address and event capacity; launch events; advertise with a QR code; order food; change dishes for guest needs; calculate total ingredients from paid attendance, plus extra; provide live order updates; show an event calendar. The Organizer brings the ingredients for each dish.
- Business objects / data entities: User, event, dish, ingredient, food order, payment, diet need, special need, food preference, QR code, event calendar.
- External integrations: UNKNOWN.
- Authentication / roles: Authentication is UNKNOWN. Named roles are Admin, Organizer, and Attendee. Role permissions are UNKNOWN.
- Regulatory or privacy constraints: UNKNOWN.

## Functional Requirements

### Event Setup

- **FR-1.1** The system MUST let an Organizer create an event.
- **FR-1.2** The system MUST let an Organizer set the price per person for an event.
- **FR-1.3** The system MUST let an Organizer select one or more dishes for an event.
- **FR-1.4** The system MUST let an Organizer specify the address for an event.
- **FR-1.5** The system MUST let an Organizer specify the maximum number of Attendees for an event.

### Event Launch and Advertising

- **FR-2.1** The system MUST let an Organizer launch an event.
- **FR-2.2** The system MUST give the Organizer a QR code for an event when the Organizer launches that event.

### Food Orders and Guest Needs

- **FR-3.1** The system MUST let an Attendee place a food order for an event.
- **FR-3.2** The system MUST let an Attendee specify diet needs for each dish in a food order.
- **FR-3.3** The system MUST let an Attendee specify special needs for each dish in a food order.
- **FR-3.4** The system MUST let an Attendee specify food preferences for each dish in a food order.

### Order Updates

- **FR-4.1** The system MUST send an order update to the cook when an Attendee places a food order for an event.
- **FR-4.2** The system MUST send an order update to the grocery shopper when an Attendee places a food order for an event.

### Event Calendar

- **FR-5.1** The system MUST show events in an event calendar.

## Non-Functional Requirements

None stated

## Open Questions

- **OQ-1** What authentication and permissions apply to each role? How do the cook and grocery shopper relate to these roles?
- **OQ-2** Which data and checks does an event need before launch? What must the system do if a check fails?
- **OQ-3** What must the system do when attendance would exceed the event capacity?
- **OQ-4** What must the QR code contain? What must happen when a person scans it?
- **OQ-5** Must the website collect payments or record payments made elsewhere? Which currency, payment statuses, and payment failure rules apply?
- **OQ-6** How does a food order relate to attendance and payment? How must the system identify the Attendees who have paid?
- **OQ-7** Where do dishes, ingredients, and quantities per dish come from? How must the system calculate total ingredients from paid attendance and dish changes? How much extra must it include?
- **OQ-8** What food rules apply to vegan, vegetarian, keto, diabetic, and other diet needs? What does "Hundu" mean in the notes?
- **OQ-9** How must the system make sure that dishes meet diet needs, special needs, and food preferences? What must happen if a request cannot be met?
- **OQ-10** What data must each order update contain, and how must each recipient receive it? What maximum delay defines "live"? What must happen if delivery fails?
- **OQ-11** Which event date and time data must the calendar show? Who can view it, and which events must it include?
