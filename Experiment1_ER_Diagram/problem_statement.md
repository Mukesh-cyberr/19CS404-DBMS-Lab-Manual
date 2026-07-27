# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="1562" height="712" alt="fitness_ER" src="https://github.com/user-attachments/assets/a8c55056-68a5-49db-9d47-bfea25fd191a" />
### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|   Member     |   member_id (PK), member_name, membership_type, start_date                 |    Stores member details   |
|   Trainer     |       trainer_id (PK), trainer_name, duty_time             |   Trainer details    |
|    Program    |program_id (PK), program_name|  Fitness program     |
| Training Session       |   session_id (PK), member_id (FK), trainer_id (FK), session_date, session_time              | Personal training      |
| Payment       |      payment_id (PK), member_id (FK), amount              |    Payments   |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|    Member attends Program           |       M:N     |    Partial           |   Members may join multiple programs |
|     Trainer teaches Program         |       M:N      |       Total        |  Programs may have multiple trainers     |
|       Member books Session        |       1:M     |      Partial          |    Member books personal sessions  |
|     Trainer conducts Session         |  1:M          |    Total           |  Trainer handles many sessions     |
|  Member makes Payment            |    1:M        |     Partial          | Membership and session fees      |


### Assumptions
-  Each member has a unique ID.
-  Attendance is recorded for every session
-  Payments include membership and personal training fees.

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
<img width="819" height="479" alt="image" src="https://github.com/user-attachments/assets/b3732d25-adb7-46fb-9ae1-74da772d1cdb" />

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|  Member      |      member_id (PK), name, phone, email               |  Library member     |
|    Book    |     book_id (PK), ISBN, title, category, publisher, publication_year               |    Book |
|   Book Author     |       author_id (PK), book_id (FK), author_name              |      Author |
|  Loan      |       loan_id (PK), loan_date, due_date, return_date, status             |    Borrow record   |
|   Fine  |       fine_id (PK), amount, paid_status, paid_dat             | Late fine   |
|    Event    |        event_id (PK), event_name, event_date, event_time, event_type            | Library event      |
|  Registration      |    registration_id (PK), registration_date, status                 |   Registration    |
|  Room      |     room_id (PK), room_name, room_type, capacity               |  Room     |


### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|     Member borrows Book         |       M:N     |       Partial        |  Resolved through Loan     |
|     Loan has Fine          |      1:0..1      |        Partial       |    Fine only for overdue books   |
|   Book written by Author           |     M:N         |        Tota       |    Books can have multiple authors|
|     Member registers Event         |     M:N         |      Partial        |  Many event registrations     |
|     Event held in Room          |     M:1       |       Total        |     Rooms reused over time  |


### Assumptions
-  Fine exists only for overdue books
-  Every event has at least one speaker.
- Rooms may host multiple events.

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="1522" height="712" alt="reservedbms drawio" src="https://github.com/user-attachments/assets/f10b0ddc-dd28-4f01-a515-7c827d98677f" />

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|  Customer   |      customer_id (PK), name, phone, email              |  Customer    |
|    Reservation  |         reservation_id (PK), date, time, reservation_type, no_of_guests        |     Reservation  |
|    Waiter |   waiter_id (PK), name, phone, section            |    Waiter    |
|    Order    |         order_id (PK), order_time, special_request           |  Order |
|     Order Item    |        order_item_id (PK), quantity, unit_price, subtotal            |    Order details   |
| Bill |bill_id (PK), bill_date, food_amount, service_charge, tax, total_amount|Bill|

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|      Customer makes Reservation         |        1:M     |      Partial          | One customer may have many reservations      |
|       Waiter serves Reservation       |    1:M         |        Total        |  Reservation assigned to one waiter |
|      Reservation has Order        | 1:M            |      Total          |   Reservation may contain many orders    |
|       Order contains Order Item       |   1:M          |      Total          | Order consists of multiple items      |
|      Reservation generates Bill        |   1:1         |          Total      |  One bill per reservation     |


### Assumptions
- Walk-in customers are stored as reservations
- One waiter serves each reservation
- One bill is generated for each reservation.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
