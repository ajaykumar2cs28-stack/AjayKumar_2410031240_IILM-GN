## Query 1: Show all bookings with customer name and room number
```sql
SELECT 
    c.Name, 
    r.Room_Number, 
    b.Check_in_Date, 
    b.Check_out_Date
FROM Booking b
JOIN Customer c ON b.Customer_ID = c.Customer_ID
JOIN Room r ON b.Room_ID = r.Room_ID;
```


## Query 2: Total revenue collected
```sql
SELECT 
    SUM(Amount) AS Total_Revenue
FROM Payment
WHERE Payment_Status = 'Paid';
```


## Query 3: Number of bookings per room type
```sql
SELECT 
    r.Room_Type, 
    COUNT(b.Booking_ID) AS Total_Bookings
FROM Room r
JOIN Booking b ON r.Room_ID = b.Room_ID
GROUP BY r.Room_Type;
```


## Query 4: Customers who paid more than 5000
```sql
SELECT 
    c.Name, 
    p.Amount
FROM Customer c
JOIN Booking b ON c.Customer_ID = b.Customer_ID
JOIN Payment p ON b.Booking_ID = p.Booking_ID
WHERE p.Amount > 5000;
```


## Query 5: Available rooms
```sql
SELECT 
    Room_Number, 
    Room_Type, 
    Price
FROM Room
WHERE Status = 'Available';
```
