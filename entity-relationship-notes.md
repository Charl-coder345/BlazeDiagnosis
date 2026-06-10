#  Task 1: Main System Entities and Relationships

## Main entities
1.	Customer
2.	Vehicle
3.	Job Card
4.	Quote
5.	Invoice
6.	Parts Order
7.	Notification
8.	Service Advisor

## Relationships

### Customer
•	Store customer information
•	Can own multiple vehicles
•	Receives notifications and invoices

### Vehicle
•	Belongs to a customer
•	Can have multiple job cards for different repairs or services

### Job Card
•	Tracks workshop work performed on a vehicle
•	Contains repair/workflow statuses
•	Linked to quotes, parts orders, and invoices

### Quote
•	Linked to a job card
•	Contains estimated repair or service costs 
•	May require customer approval

### Invoice
•	Linked to customer, vehicle, and job card
•	Generated from approved quotes

### Parts Order
•	Linked to job card 
•	Tracks parts required for repairs or services
•	May affect repair progress/status

### Notification
•	Sent to customers for important updates
•	May notify service advisors about quote approvals, parts updates, or job status changes

### Service Advisor
-	Creates customer profiles
-	Registers customer vehicles
-	Creates and manages job cards
-	Updates repair/ job status
-	Communicates with customers

### Mapping
Customer
   ↓ owns
Vehicle
   ↓ has
Job Card
   ↓ linked to
Quote
   ↓ approved into
Invoice

Job Card
   ↓ may require
Parts Order

Job Card
   ↓ triggers
Notification

Service Advisor
   ↓ manages
Customer, Vehicle, and Job Card
