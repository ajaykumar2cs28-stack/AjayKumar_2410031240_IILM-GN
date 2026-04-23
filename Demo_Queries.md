# Important SQL Queries - Hotel Room Booking System
```sql
## 1. Show All Customers
SELECT * FROM Customer;
## 2. Show Available Rooms
SELECT * FROM Room
WHERE Status = 'Available';
## 3. Booking Details Using JOIN
SELECT c.Name, r.Room_Number, r.Room_Type,
       b.Check_in_Date, b.Check_out_Date
FROM Booking b
JOIN Customer c ON b.Customer_ID = c.Customer_ID
JOIN Room r ON b.Room_ID = r.Room_ID;
## 4. Total Revenue Received
SELECT SUM(Amount) AS Total_Revenue
FROM Payment
WHERE Payment_Status = 'Paid';
## 5. Count Bookings by Room Type
SELECT r.Room_Type, COUNT(*) AS Total_Bookings
FROM Booking b
JOIN Room r ON b.Room_ID = r.Room_ID
GROUP BY r.Room_Type;
## 6. Average Room Price
SELECT AVG(Price) AS Average_Price
FROM Room;
## 7. Highest Paying Customer
SELECT c.Name, SUM(p.Amount) AS TotalSpent
FROM Customer c
JOIN Booking b ON c.Customer_ID = b.Customer_ID
JOIN Payment p ON b.Booking_ID = p.Booking_ID
GROUP BY c.Name
ORDER BY TotalSpent DESC
LIMIT 1;
## 8. Customers With Pending Payment
SELECT c.Name, p.Amount
FROM Customer c
JOIN Booking b ON c.Customer_ID = b.Customer_ID
JOIN Payment p ON b.Booking_ID = p.Booking_ID
WHERE p.Payment_Status = 'Pending';
## 9. Rooms Never Booked (Subquery)
SELECT Room_Number
FROM Room
WHERE Room_ID NOT IN
(SELECT Room_ID FROM Booking);
## 10. Rooms Sorted by Highest Price
SELECT * FROM Room
ORDER BY Price DESC;
