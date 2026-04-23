# Module 3 - Normalization and BCNF Analysis
## Project Title:
Hotel Room Booking System
---
## Introduction
Normalization is the process of organizing data in a database to reduce redundancy and improve consistency.
The Hotel Room Booking System database has been normalized into separate tables:
- Customer
- Room
- Booking
- Payment
This improves efficiency and avoids duplicate data.
---
## Unnormalized Form (UNF)
If all data were stored in one table:
| Customer Name | Phone | Room Number | Room Type | Booking Date | Payment Method |
|--------------|-------|------------|----------|-------------|----------------|
This causes:
- Repetition of customer details
- Repetition of room details
- Data inconsistency
- Difficult updates
---
## First Normal Form (1NF)
Rules:
- Atomic values
- No repeating groups
Applied by creating columns with single values such as:
- Name
- Phone
- Room_Number
- Payment_Method
Thus database satisfies 1NF.
---
## Second Normal Form (2NF)
Rules:
- Must be in 1NF
- No partial dependency
Applied by separating data into tables:
- Customer table stores customer details
- Room table stores room details
- Booking table stores booking records
Thus database satisfies 2NF.
---
## Third Normal Form (3NF)
Rules:
- Must be in 2NF
- No transitive dependency
Applied by storing payment details in separate Payment table.
Thus database satisfies 3NF.
---
## Boyce-Codd Normal Form (BCNF)
Rule:
Every determinant must be a candidate key.
Examples:
- Customer_ID → Name, Address, Email, Phone
- Room_ID → Room_Number, Room_Type, Price, Status
- Booking_ID → Customer_ID, Room_ID, Dates
- Payment_ID → Booking_ID, Amount, Status
All determinants are keys.
Thus database satisfies BCNF.
---
## Tools used for normalization
### MySQL Workbench
---
## Functional Dependencies
### Customer Table
Customer_ID → Name, Address, Email, Phone
### Room Table
Room_ID → Room_Number, Room_Type, Price, Status
### Booking Table
Booking_ID → Customer_ID, Room_ID, Check_in_Date, Check_out_Date
### Payment Table
Payment_ID → Booking_ID, Amount, Payment_Method, Payment_Status
---
## Conclusion
The Hotel Room Booking System database is properly normalized up to BCNF.  
This reduces redundancy, improves consistency, and ensures efficient data management.
