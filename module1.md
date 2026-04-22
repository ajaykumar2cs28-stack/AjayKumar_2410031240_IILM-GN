# Hotel Room Booking System - Module 1

## Create Database

```sql
CREATE DATABASE HotelManagementSystem;
USE HotelManagementSystem;


CREATE TABLE Customer (
    Customer_ID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100) NOT NULL,
    Address VARCHAR(200),
    Email VARCHAR(100),
    Phone VARCHAR(15)
);

CREATE TABLE Room (
    Room_ID INT PRIMARY KEY AUTO_INCREMENT,
    Room_Number VARCHAR(10) UNIQUE NOT NULL,
    Room_Type VARCHAR(50),
    Price DECIMAL(10,2),
    Status VARCHAR(20)
);

CREATE TABLE Booking (
    Booking_ID INT PRIMARY KEY AUTO_INCREMENT,
    Customer_ID INT,
    Room_ID INT,
    Check_in_Date DATE,
    Check_out_Date DATE,
    Booking_Date DATE,
    Total_Amount DECIMAL(10,2),

    FOREIGN KEY (Customer_ID)
        REFERENCES Customer(Customer_ID)
        ON DELETE CASCADE,

    FOREIGN KEY (Room_ID)
        REFERENCES Room(Room_ID)
        ON DELETE CASCADE
);

CREATE TABLE Payment (
    Payment_ID INT PRIMARY KEY AUTO_INCREMENT,
    Booking_ID INT UNIQUE,
    Amount DECIMAL(10,2),
    Payment_Method VARCHAR(50),
    Payment_Date DATE,
    Payment_Status VARCHAR(30),

    FOREIGN KEY (Booking_ID)
        REFERENCES Booking(Booking_ID)
        ON DELETE CASCADE
);
