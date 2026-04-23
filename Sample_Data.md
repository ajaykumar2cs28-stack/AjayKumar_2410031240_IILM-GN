# Sample Data - Hotel Room Booking System
## Customer Table
| Customer_ID | Name         | Address     | Email            | Phone      |
|------------|--------------|------------|------------------|-----------|
| 1 | Amit Sharma | Delhi      | amit@gmail.com   | 9876543210 |
| 2 | Riya Verma  | Noida      | riya@gmail.com   | 9876501234 |
| 3 | Karan Singh | Gurgaon    | karan@gmail.com  | 9811122233 |
| 4 | Neha Gupta  | Faridabad  | neha@gmail.com   | 9898989898 |
| 5 | Rahul Yadav | Delhi      | rahul@gmail.com  | 9999911111 |
---
## Room Table
| Room_ID | Room_Number | Room_Type | Price | Status |
|--------|------------|----------|------|--------|
| 1 | 101 | Deluxe   | 5000 | Booked |
| 2 | 102 | Standard | 3000 | Available |
| 3 | 103 | Suite    | 8000 | Booked |
| 4 | 104 | Deluxe   | 5200 | Available |
| 5 | 105 | Standard | 3200 | Booked |
---
## Booking Table
| Booking_ID | Customer_ID | Room_ID | Check_in_Date | Check_out_Date | Booking_Date | Total_Amount |
|-----------|------------|--------|--------------|---------------|-------------|-------------|
| 1 | 1 | 1 | 2026-04-20 | 2026-04-22 | 2026-04-18 | 10000 |
| 2 | 2 | 3 | 2026-04-21 | 2026-04-23 | 2026-04-19 | 16000 |
| 3 | 3 | 5 | 2026-04-22 | 2026-04-24 | 2026-04-20 | 6400 |
| 4 | 4 | 1 | 2026-04-25 | 2026-04-26 | 2026-04-21 | 5000 |
---
## Payment Table
| Payment_ID | Booking_ID | Amount | Payment_Method | Payment_Date | Payment_Status |
|-----------|-----------|-------|----------------|-------------|---------------|
| 1 | 1 | 10000 | UPI  | 2026-04-18 | Paid |
| 2 | 2 | 16000 | Card | 2026-04-19 | Paid |
| 3 | 3 | 6400  | Cash | 2026-04-20 | Pending |
| 4 | 4 | 5000  | UPI  | 2026-04-21 | Paid |
