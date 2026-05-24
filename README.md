# Event Management System

A relational database solution that centralizes event operations managing clients, vendors, bookings, tasks, invoices, and feedback through a normalized 10-entity schema built for accuracy, efficiency, and end-to-end event lifecycle visibility.

---

## Problem Statement

Event logistics are inherently complex. Coordinating clients, vendors, staff, bookings, and payments across multiple touchpoints leads to fragmented data and operational inefficiency. This system provides a structured, database-driven foundation that brings all event management operations under one roof.

## Features

- Client and vendor relationship management
- End-to-end booking and event request tracking
- Task assignment with deadlines and staff accountability
- Invoice and payment lifecycle management
- Post-event feedback collection and staff linkage
- Schema migration support via UP/DOWN scripts
- PowerApps integration for front-end automation

---

## Database Schema

The system is built around 10 core entities:

| Entity | Key Attributes |
|---|---|
| `Clients` | client_id, name, contact_details, location_id, invoice_id |
| `Locations` | location_id, city_name, location_type, max_occupancy |
| `Events` | event_id, event_date, event_type, guest_count, location_id, client_id |
| `Event Requests` | request_id, requesting_client_id, event_date, guest_count, approval_status |
| `Staff` | staff_id, name, position, contact_details |
| `Tasks` | task_id, assigned_staff, event_id, deadline |
| `Vendors` | vendor_id, vendor_name, contact_details |
| `Invoices` | invoice_id, invoice_date_issued, status, vendor_id, client_id |
| `Payments` | payment_id, amount, date, method, invoice_id, client_id |
| `Feedbacks` | feedback_id, rating, comment, client_id, event_id, staff_id |

---

## Entity Relationships

**One-to-Many**
- A client may have multiple locations, invoices, and events
- A location may host multiple events
- A vendor may issue multiple invoices
- An event may receive multiple feedback entries
- A staff member may be assigned multiple tasks

**Many-to-Many**
- Locations ↔ Vendors: vendors service multiple locations
- Clients ↔ Vendors: clients engage multiple vendors

**One-to-One**
- Invoice ↔ Payment: each invoice maps to a single payment
- Event Request ↔ Event: each approved request produces one event
- Event Request ↔ Client: each request is tied to one requesting client

---

## Implementation

The database includes **UP** and **DOWN** migration scripts for controlled schema versioning. Conceptual and logical data models are documented separately to support architecture review and onboarding.

---

## Roadmap

- [ ] Automated invoice generation and payment reminders
- [ ] AI-assisted event planning recommendations
- [ ] Real-time event monitoring and reporting dashboard

---

## Author

**Nithin Kumar**

