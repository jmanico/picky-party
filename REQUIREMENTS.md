# Requirements

The project notes define the purpose and core workflows. Existing requirement IDs remain stable.

ASSUMPTION: All added policies, limits, and numerical targets are product decisions made at the user's request. They are requirements for the first release, not measured results. External facts that the notes do not provide remain UNKNOWN.

## Required Requirement Inputs

- Project purpose: A cooking event website with a price per person, dishes that meet guest needs, and ingredient planning for the Organizer.
- Primary users / actors: Admin, Organizer, Attendee; cook and grocery shopper. ASSUMPTION: Cook and shopper are event assignments, not additional account roles.
- Core workflows: Create and launch events; advertise with QR codes; review food requests; take payment; confirm attendance; calculate ingredients; update event staff; cancel and refund bookings; show an event calendar.
- Business objects / data entities: Account, event, staff assignment, dish, recipe, ingredient, food order, dietary request, seat hold, booking, payment, refund, payout, order update, QR code.
- External integrations: ASSUMPTION: A payment service for online checkout, refunds, and Organizer payouts; an email service for account access and notices. Provider selection is TO BE DECIDED during implementation.
- Authentication / roles: ASSUMPTION: Verified email access. Accounts can hold Organizer and Attendee roles. Admin controls Admin access. Event assignments grant limited staff access.
- Regulatory or privacy constraints: Applicable jurisdictions and statutory duties are UNKNOWN. ASSUMPTION: Private dietary data needs consent; exact addresses have restricted access; the retention rules below apply.

### Adopted Decisions

All entries in this table are ASSUMPTION. They resolve the former open questions.

| Former question | Decision |
| --- | --- |
| OQ-1 | Verified accounts; event ownership; cook and shopper assignments; Admin oversight. See FR-6. |
| OQ-2 | Launch requires complete event data, recipes, and an enabled payment account. Failed checks preserve the draft. See FR-1 and FR-2. |
| OQ-3 | Confirmed bookings and unexpired seat holds consume capacity. No waitlist. See FR-8. |
| OQ-4 | The QR code opens the public event page at a permanent event URL. See FR-2. |
| OQ-5 | Online USD payments only; full payment per seat; full refunds for eligible cancellations; no platform fee. See FR-8 and FR-9. |
| OQ-6 | One account books one seat per event. Only confirmed, uncancelled bookings count as paid attendance. See FR-8 and FR-10. |
| OQ-7 | Organizer supplies recipes for one portion. Shopping totals use confirmed recipe quantities plus 10% extra. See FR-7 and FR-10. |
| OQ-8 | Interpret "Hundu" as Hindu. Labels describe guest requests; explicit restrictions and Organizer review determine each dish. See FR-3. |
| OQ-9 | Every food change needs Organizer approval and Attendee acceptance before payment. Unmet needs block payment. See FR-3. |
| OQ-10 | Staff receive persistent website updates. Under the stated load, 95% arrive within five seconds and all within 30 seconds. See FR-4 and NFR-1. |
| OQ-11 | Public month and list views show launched, upcoming events. Times use the event time zone. See FR-5. |

### Product Rules and Terms

- An event has one Organizer, one address, one start time, one end time, and one time zone. The Organizer supplies ingredients.
- A complete address contains a street address, city, and country. Postal code, region, and access instructions are optional.
- An event is Draft, Launched, Cancelled, or Completed. Completion occurs at the scheduled end time unless the event is Cancelled.
- The booking cutoff is 24 hours before the start time. Launch must occur before this cutoff. Orders, payment, and Attendee cancellations close at the cutoff.
- A seat includes one portion of each event dish. An approved omission removes that portion. Food changes do not change the seat price.
- Each food order belongs to one Attendee and one event. Order states are Draft, Pending Review, Rejected, Ready for Payment, Payment Pending, Confirmed, Cancelled, and Expired.
- Active orders are Draft, Pending Review, Ready for Payment, Payment Pending, or Confirmed. An approved proposal remains Pending Review until Attendee acceptance.
- Payment states are Pending, Paid, Failed, and Expired. Refund states are Not Requested, Pending, Refunded, and Failed. Refund state does not restore a cancelled booking.
- A seat hold lasts 15 minutes, or until the booking cutoff, whichever occurs first. Pending review and approval do not reserve seats.
- A published event keeps its price, currency, menu, base recipes, address, and schedule. The Organizer can change its title, description, staff, and valid capacity.
- Dietary labels are vegan, vegetarian, keto, Hindu, diabetic, and other. No label alone certifies a dish or defines medical suitability.
- The first release supports English and USD. Group bookings, extra portions, offline payments, waitlists, discounts, and automatic dietary certification are outside its scope.

## Functional Requirements

### Event Setup

- **FR-1.1** The system MUST let an Organizer create an event.
- **FR-1.2** The system MUST let an Organizer set the price per person for an event.
- **FR-1.3** The system MUST let an Organizer select one or more dishes for an event.
- **FR-1.4** The system MUST let an Organizer specify the address for an event.
- **FR-1.5** The system MUST let an Organizer specify the maximum number of Attendees for an event.
- **FR-1.6** The system MUST save a new event as a private Draft.
- **FR-1.7** The system MUST let the event Organizer enter its title, description, start time, end time, and time zone.
- **FR-1.8** The system MUST reject a capacity that is not a positive whole number.
- **FR-1.9** The system MUST reject a price that is not a positive USD amount with at most two decimal places.
- **FR-1.10** The system MUST reject an end time that is not after the start time.
- **FR-1.11** The system MUST reject a local time that is invalid or ambiguous until the Organizer selects a valid, unambiguous time.
- **FR-1.12** The system MUST identify each invalid field when it rejects event data.
- **FR-1.13** The system MUST preserve entered values when it rejects event data.
- **FR-1.14** The system MUST let the event Organizer preview the public event details before launch.

### Event Launch and Advertising

- **FR-2.1** The system MUST let an Organizer launch an event.
- **FR-2.2** The system MUST give the Organizer a QR code for an event when the Organizer launches that event.
- **FR-2.3** The system MUST reject launch if the title, description, complete address, schedule, capacity, price, or menu is missing.
- **FR-2.4** The system MUST reject launch if any menu dish lacks a complete recipe for one portion.
- **FR-2.5** The system MUST reject launch unless the Organizer's payment account can accept payments and receive payouts.
- **FR-2.6** The system MUST reject launch at or after the booking cutoff.
- **FR-2.7** The system MUST keep an event in Draft when a launch check fails.
- **FR-2.8** The system MUST publish a launched event at a permanent public URL.
- **FR-2.9** The system MUST encode only the public event URL in its QR code.
- **FR-2.10** The system MUST let the event Organizer download the QR code.
- **FR-2.11** The system MUST show the title, description, Organizer name, menu, schedule, city, country, price, cutoff, and available seats on the public page.
- **FR-2.12** The system MUST restrict the exact event address to its Organizer, assigned staff, confirmed Attendees, and Admin.
- **FR-2.13** The system MUST reject changes to the fixed event fields listed in Product Rules after launch.
- **FR-2.14** The system MUST reject a capacity reduction below confirmed bookings plus unexpired seat holds.
- **FR-2.15** The system MUST retain a cancelled event's public URL with a cancellation notice.
- **FR-2.16** The system MUST mark a launched event Completed at its end time.

### Food Orders and Guest Needs

- **FR-3.1** The system MUST let an Attendee place a food order for an event.
- **FR-3.2** The system MUST let an Attendee specify diet needs for each dish in a food order.
- **FR-3.3** The system MUST let an Attendee specify special needs for each dish in a food order.
- **FR-3.4** The system MUST let an Attendee specify food preferences for each dish in a food order.
- **FR-3.5** The system MUST include one portion of every menu dish in a new order.
- **FR-3.6** The system MUST offer all dietary labels listed in Product Rules for each dish.
- **FR-3.7** The system MUST require explicit restrictions for each selected dietary label.
- **FR-3.8** The system MUST let an Attendee record ingredient exclusions and cross-contact concerns for each dish.
- **FR-3.9** The system MUST let an Attendee request omission of a dish.
- **FR-3.10** The system MUST require consent before sharing food needs with the event Organizer and cook.
- **FR-3.11** The system MUST place an order with food needs or changes in Pending Review after submission.
- **FR-3.12** The system MUST place an unchanged order in Ready for Payment after submission.
- **FR-3.13** The system MUST show the event Organizer every request in an order awaiting review.
- **FR-3.14** The system MUST let the event Organizer propose a complete recipe or omission for each requested dish change.
- **FR-3.15** The system MUST require the Organizer to confirm that each proposed dish meets every recorded request before approval.
- **FR-3.16** The system MUST show the Attendee the proposed ingredients, omissions, and handling notes before acceptance.
- **FR-3.17** The system MUST move an approved order to Ready for Payment only after the Attendee accepts the proposed dishes.
- **FR-3.18** The system MUST let the event Organizer reject a request with a reason.
- **FR-3.19** The system MUST block payment for orders with unresolved or rejected requests.
- **FR-3.20** The system MUST let an Attendee revise an unpaid order before the cutoff when it has no active seat hold.
- **FR-3.21** The system MUST require a new review when an Attendee changes a previously approved food request.
- **FR-3.22** The system MUST reject food changes after payment confirmation.
- **FR-3.23** The system MUST show dietary labels as requests rather than medical or dietary certifications.
- **FR-3.24** The system MUST expire unconfirmed orders at the booking cutoff.

### Order Updates

- **FR-4.1** The system MUST send an order update to the cook when an Attendee places a food order for an event.
- **FR-4.2** The system MUST send an order update to the grocery shopper when an Attendee places a food order for an event.
- **FR-4.3** The system MUST update assigned staff views after an order revision, review decision, payment confirmation, cancellation, or refund result.
- **FR-4.4** The system MUST show the order reference, state, change time, and paid-attendance effect in each staff update.
- **FR-4.5** The system MUST show the cook the Attendee name, dish quantities, approved recipes, and food needs for confirmed orders.
- **FR-4.6** The system MUST show the shopper the ingredient changes and current shopping totals in each update.
- **FR-4.7** The system MUST exclude Attendee names and private food notes from shopper views.
- **FR-4.8** The system MUST mark unconfirmed orders as excluded from preparation and shopping totals.
- **FR-4.9** The system MUST retain order updates while the event remains active.
- **FR-4.10** The system MUST show the current event state and missed updates when staff reconnect.
- **FR-4.11** The system MUST show a disconnected status with the last successful update time when a staff view loses its connection.
- **FR-4.12** The system MUST send email notices for review decisions, booking confirmation, event cancellation, and refund results.
- **FR-4.13** The system MUST keep notices available in the account if email delivery fails.
- **FR-4.14** The system MUST exclude exact addresses and private food notes from email notices.

### Event Calendar

- **FR-5.1** The system MUST show events in an event calendar.
- **FR-5.2** The system MUST give visitors month and chronological list views of launched events that have not ended.
- **FR-5.3** The system MUST show each event's title, start time, end time, time zone, city, price, and booking availability in calendar views.
- **FR-5.4** The system MUST place each event on its start date in the event time zone.
- **FR-5.5** The system MUST let visitors filter calendar events by date range and city.
- **FR-5.6** The system MUST open the public event page when a visitor selects a calendar event.
- **FR-5.7** The system MUST mark full events and events past the cutoff as closed for booking.
- **FR-5.8** The system MUST exclude Draft, Cancelled, and Completed events from the public calendar.
- **FR-5.9** The system MUST show an Attendee their confirmed and cancelled bookings in their account.
- **FR-5.10** The system MUST show an Organizer their events in every event state.

### Accounts, Roles, and Staff

- **FR-6.1** The system MUST let a person create an account with a display name and email address.
- **FR-6.2** The system MUST require email verification before an account can place orders or create events.
- **FR-6.3** The system MUST let a verified account sign in through an email link.
- **FR-6.4** The system MUST let a signed-in account end its session.
- **FR-6.5** The system MUST let a verified account act as both Organizer and Attendee.
- **FR-6.6** The system MUST restrict changes to an event to its Organizer, except the Admin actions specified below.
- **FR-6.7** The system MUST restrict order changes to the order's Attendee and the Organizer review actions specified above.
- **FR-6.8** The system MUST assign the event Organizer as its initial cook and shopper.
- **FR-6.9** The system MUST let the event Organizer grant or remove cook and shopper assignments for verified accounts.
- **FR-6.10** The system MUST restrict staff access to events with a current assignment.
- **FR-6.11** The system MUST permit only an Admin to grant or remove the Admin role.
- **FR-6.12** The system MUST let an Admin suspend an account from new events and orders.
- **FR-6.13** The system MUST preserve cancellation and refund access for existing bookings when an account is suspended.
- **FR-6.14** The system MUST let an Admin cancel a launched event before its start time with a recorded reason.
- **FR-6.15** The system MUST let an Admin inspect payment and refund failures.
- **FR-6.16** The system MUST reject an unauthorized action without changing the affected record.
- **FR-6.17** The system MUST let an Admin restore a suspended account's access to new events and orders.

### Dishes and Recipes

- **FR-7.1** The system MUST let an Organizer create a named dish with ingredients and quantities for one portion.
- **FR-7.2** The system MUST let an Organizer reuse a dish in multiple events.
- **FR-7.3** The system MUST require an ingredient name, quantity, and unit for each recipe entry.
- **FR-7.4** The system MUST reject ingredient quantities that are not positive numbers.
- **FR-7.5** The system MUST accept ingredient quantities in grams, kilograms, millilitres, litres, or count.
- **FR-7.6** The system MUST let the Organizer select a shared ingredient record across recipes.
- **FR-7.7** The system MUST keep distinct ingredient variants in separate records.
- **FR-7.8** The system MUST keep a launched event's recipes unchanged when the Organizer edits a reusable dish.
- **FR-7.9** The system MUST preserve the accepted recipe for each confirmed order.
- **FR-7.10** The system MUST show complete ingredient lists to the Attendee before payment.

### Seats and Payments

- **FR-8.1** The system MUST restrict new orders to launched events before their booking cutoff.
- **FR-8.2** The system MUST permit at most one active order per Attendee for each event.
- **FR-8.3** The system MUST reserve one seat when a Ready for Payment order enters checkout.
- **FR-8.4** The system MUST reject checkout when confirmed bookings plus unexpired seat holds equal event capacity.
- **FR-8.5** The system MUST prevent simultaneous checkout requests from reserving the same remaining seat.
- **FR-8.6** The system MUST show the seat hold expiry time before payment.
- **FR-8.7** The system MUST release a seat hold when payment fails, checkout is cancelled, or the hold expires.
- **FR-8.8** The system MUST return an unsuccessful checkout order to Ready for Payment before the cutoff once its payment result confirms no charge.
- **FR-8.9** The system MUST show the final USD price and cancellation terms before payment.
- **FR-8.10** The system MUST collect the full event price for one seat through the payment service.
- **FR-8.11** The system MUST exclude additional Attendee fees from checkout.
- **FR-8.12** The system MUST confirm a booking only after the payment service confirms the correct amount and currency during a valid seat hold.
- **FR-8.13** The system MUST record the payment reference and payment state against the order.
- **FR-8.14** The system MUST create at most one confirmed booking from repeated payment confirmations for the same order.
- **FR-8.15** The system MUST request a full refund for a payment received after hold expiry or event cancellation.
- **FR-8.16** The system MUST request a full refund for an incorrect or duplicate payment.
- **FR-8.17** The system MUST exclude payments awaiting validation from confirmed attendance.
- **FR-8.18** The system MUST show the Attendee the confirmed booking reference and receipt after payment confirmation.
- **FR-8.19** The system MUST preserve a payment's Pending state while the payment service cannot determine its result.
- **FR-8.20** The system MUST block another payment for an Attendee's event while that Attendee has an unresolved payment for the same event.
- **FR-8.21** The system MUST let an Admin reconcile an unknown payment result against the payment service record.
- **FR-8.22** The system MUST let an Organizer connect a payment service account for event payments and payouts.
- **FR-8.23** The system MUST show the Organizer whether the connected payment account can accept payments and receive payouts.
- **FR-8.24** The system MUST replace the seat hold with one confirmed booking when it confirms payment.

### Cancellations, Refunds, and Payouts

- **FR-9.1** The system MUST let an Attendee cancel a confirmed booking before the booking cutoff.
- **FR-9.2** The system MUST reject Attendee cancellation at or after the booking cutoff.
- **FR-9.3** The system MUST release a confirmed seat when its booking is cancelled.
- **FR-9.4** The system MUST request a full refund when an Attendee makes an eligible cancellation.
- **FR-9.5** The system MUST let the event Organizer cancel a launched event before its start time.
- **FR-9.6** The system MUST cancel all active orders when an event is cancelled.
- **FR-9.7** The system MUST request a full refund for each paid booking when an event is cancelled.
- **FR-9.8** The system MUST show Pending until the payment service confirms a refund result.
- **FR-9.9** The system MUST show a failed refund to the affected Attendee, event Organizer, and Admin.
- **FR-9.10** The system MUST let an Admin retry a failed refund without exceeding the amount originally paid.
- **FR-9.11** The system MUST keep a cancelled booking excluded from attendance while its refund is pending or failed.
- **FR-9.12** The system MUST show the Organizer collected payments, refunds, payment service fees, and net proceeds for each event.
- **FR-9.13** The system MUST request the Organizer's payout after event completion, excluding unresolved payments and amounts owed as refunds.
- **FR-9.14** The system MUST show the Organizer each payout's amount and provider status.
- **FR-9.15** The system MUST notify the Organizer and Admin when a payout fails.
- **FR-9.16** The system MUST cap total refunds for each payment at the amount received.
- **FR-9.17** The system MUST let an Admin retry a failed payout.
- **FR-9.18** The system MUST prevent repeated payout requests from paying the same event proceeds more than once.

### Ingredient Planning

For each shared ingredient record and unit family, base quantity is the sum of its quantities in all confirmed, uncancelled orders. An accepted replacement uses its own recipe instead of the original recipe. An omitted dish contributes zero. Shopping quantity is base quantity multiplied by 1.10, rounded upward to the next whole gram, millilitre, or count. Zero base quantity produces zero shopping quantity.

- **FR-10.1** The system MUST show the event Organizer the count of confirmed, uncancelled Attendees.
- **FR-10.2** The system MUST calculate base ingredient quantities from the accepted recipes of confirmed, uncancelled orders.
- **FR-10.3** The system MUST exclude unconfirmed and cancelled orders from all ingredient totals.
- **FR-10.4** The system MUST convert kilograms to grams at 1,000 grams per kilogram before adding quantities.
- **FR-10.5** The system MUST convert litres to millilitres at 1,000 millilitres per litre before adding quantities.
- **FR-10.6** The system MUST keep mass, volume, and count quantities in separate totals.
- **FR-10.7** The system MUST group quantities only when they use the same ingredient record and unit family.
- **FR-10.8** The system MUST calculate shopping quantities with the stated 10% extra and upward rounding rule.
- **FR-10.9** The system MUST show base quantity, extra quantity, and shopping quantity for each ingredient total.
- **FR-10.10** The system MUST show the number of portions for each base dish and approved dish variant.
- **FR-10.11** The system MUST recalculate ingredient totals after booking confirmation or cancellation.
- **FR-10.12** The system MUST let the event Organizer and shopper print the current shopping list with its calculation time.
- **FR-10.13** The system MUST keep each approved variant's recipe and handling notes separate in the cook view.

Acceptance examples: Ten confirmed portions at 100 grams require 1,000 grams base and 1,100 grams shopping quantity. Three portions at one egg require four eggs after rounding. Cancelling two of the ten portions reduces the shopping quantity to 880 grams.

### Privacy and Records

- **FR-11.1** The system MUST exclude orders, dietary requests, payment records, and staff updates from public event pages.
- **FR-11.2** The system MUST show each Attendee only their own order and payment records.
- **FR-11.3** The system MUST record the actor, time, and outcome of event, order, staff-assignment, and financial state changes.
- **FR-11.4** The system MUST remove private food notes 90 days after event completion or cancellation.
- **FR-11.5** The system MUST retain payment references, amounts, states, and financial action records for 24 months after their last change.
- **FR-11.6** The system MUST exclude private food notes from retained financial records.
- **FR-11.7** The system MUST let an Attendee withdraw consent for food notes by cancelling an eligible booking and deleting those notes.

## Non-Functional Requirements

ASSUMPTION: These are first-release acceptance targets. Performance measurements use 1,000 launched events, 10,000 confirmed bookings, 200 active sessions, and 20 user actions per second. Update timing starts when the system accepts a change and ends when the connected view displays it. Read timing runs from receipt of a request to delivery of its complete result. Payment service processing and email delivery have separate provider durations, which are UNKNOWN.

### Response and Update Times

- **NFR-1.1** The system MUST show accepted order changes in connected staff views within five seconds for at least 95% of updates.
- **NFR-1.2** The system MUST show all accepted order changes in connected staff views within 30 seconds under the stated load.
- **NFR-1.3** The system MUST restore current staff data within ten seconds after a connection returns under the stated load.
- **NFR-1.4** The system MUST complete event-page, calendar, and account reads within two seconds for at least 95% of requests under the stated load.
- **NFR-1.5** The system MUST submit an authorized refund request to an available payment service within one minute.

### Reliability and Consistency

- **NFR-2.1** The system MUST preserve acknowledged event and order changes across page reloads and service restarts.
- **NFR-2.2** The system MUST keep confirmed bookings plus unexpired seat holds at or below event capacity under simultaneous requests.
- **NFR-2.3** The system MUST produce identical ingredient totals for identical confirmed orders, recipes, and calculation rules.
- **NFR-2.4** The system MUST provide public event reads and signed-in account reads for at least 99.5% of each calendar month.

Availability is the percentage of successful one-minute read probes across both read types. Planned downtime counts as unavailable.

### Accessibility and Device Support

- **NFR-3.1** The system MUST make every user action available through a keyboard.
- **NFR-3.2** The system MUST provide an accessible name for each control.
- **NFR-3.3** The system MUST identify errors and state changes with text rather than color alone.
- **NFR-3.4** The system MUST keep text and actions usable at 200% text size.
- **NFR-3.5** The system MUST support a 320-pixel viewport without horizontal scrolling for forms, event details, and list views.
- **NFR-3.6** The system MUST preserve reading position and keyboard focus when a live update arrives.

## Open Questions

None remain for the defined first-release behavior. Former OQ-1 through OQ-11 are resolved in Adopted Decisions. Provider selection and jurisdiction facts remain explicitly marked inputs.
