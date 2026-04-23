-- ==========================================
-- HOTEL ROOM BOOKING SYSTEM
-- SAMPLE DATA + IMPORTANT QUERIES
-- Copy paste into XAMPP phpMyAdmin / MySQL
-- ==========================================
USE HotelManagementSystem;
-- ==========================================
-- INSERT DATA INTO CUSTOMER
-- ==========================================
INSERT INTO Customer (Name, Address, Email, Phone) VALUES
('Amit Sharma', 'Delhi', 'amit@gmail.com', '9876543210'),
('Riya Verma', 'Noida', 'riya@gmail.com', '9876501234'),
('Karan Singh', 'Gurgaon', 'karan@gmail.com', '9811122233'),
('Neha Gupta', 'Faridabad', 'neha@gmail.com', '9898989898'),
('Rahul Yadav', 'Delhi', 'rahul@gmail.com', '9999911111');
-- ==========================================
-- INSERT DATA INTO ROOM
-- ==========================================
INSERT INTO Room (Room_Number, Room_Type, Price, Status) VALUES
('101', 'Deluxe', 5000, 'Booked'),
('102', 'Standard', 3000, 'Available'),
('103', 'Suite', 8000, 'Booked'),
('104', 'Deluxe', 5200, 'Available'),
('105', 'Standard', 3200, 'Booked');
-- ==========================================
-- INSERT DATA INTO BOOKING
-- ==========================================
INSERT INTO Booking
(Customer_ID, Room_ID, Check_in_Date, Check_out_Date, Booking_Date, Total_Amount)
VALUES
(1, 1, '2026-04-20', '2026-04-22', '2026-04-18', 10000),
(2, 3, '2026-04-21', '2026-04-23', '2026-04-19', 16000),
(3, 5, '2026-04-22', '2026-04-24', '2026-04-20', 6400),
(4, 1, '2026-04-25', '2026-04-26', '2026-04-21', 5000);
-- ==========================================
-- INSERT DATA INTO PAYMENT
-- ==========================================
INSERT INTO Payment
(Booking_ID, Amount, Payment_Method, Payment_Date, Payment_Status)
VALUES
(1, 10000, 'UPI', '2026-04-18', 'Paid'),
(2, 16000, 'Card', '2026-04-19', 'Paid'),
(3, 6400, 'Cash', '2026-04-20', 'Pending'),
(4, 5000, 'UPI', '2026-04-21', 'Paid');
-- ==========================================
-- IMPORTANT QUERIES FOR DEMO
-- ==========================================
-- 1. Show all customers
SELECT * FROM Customer;
-- 2. Show available rooms
SELECT * FROM Room
WHERE Status = 'Available';
-- 3. Booking details using JOIN
SELECT c.Name, r.Room_Number, r.Room_Type,
b.Check_in_Date, b.Check_out_Date
FROM Booking b
JOIN Customer c ON b.Customer_ID = c.Customer_ID
JOIN Room r ON b.Room_ID = r.Room_ID;
-- 4. Total revenue received
SELECT SUM(Amount) AS Total_Revenue
FROM Payment
WHERE Payment_Status = 'Paid';
-- 5. Count bookings by room type
SELECT r.Room_Type, COUNT(*) AS Total_Bookings
FROM Booking b
JOIN Room r ON b.Room_ID = r.Room_ID
GROUP BY r.Room_Type;
-- 6. Average room price
SELECT AVG(Price) AS Average_Price
FROM Room;
-- 7. Highest paying customer
SELECT c.Name, SUM(p.Amount) AS TotalSpent
FROM Customer c
JOIN Booking b ON c.Customer_ID = b.Customer_ID
JOIN Payment p ON b.Booking_ID = p.Booking_ID
GROUP BY c.Name
ORDER BY TotalSpent DESC
LIMIT 1;
-- 8. Customers with pending payment
SELECT c.Name, p.Amount
FROM Customer c
JOIN Booking b ON c.Customer_ID = b.Customer_ID
JOIN Payment p ON b.Booking_ID = p.Booking_ID
WHERE p.Payment_Status = 'Pending';
-- 9. Rooms never booked (Subquery)
SELECT Room_Number
FROM Room
WHERE Room_ID NOT IN
(SELECT Room_ID FROM Booking);
-- 10. Rooms sorted by highest price
SELECT * FROM Room
ORDER BY Price DESC;






