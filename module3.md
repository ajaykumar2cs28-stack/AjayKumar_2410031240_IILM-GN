## Database Normalization

This Hotel Management System database is designed using normalization principles to reduce data redundancy and improve consistency.

### First Normal Form (1NF)

- Each table has a primary key.
- Each column stores atomic (single) values.
- No repeating groups are used.

Example:
- Customer phone number stored in one field.
- One booking record represents one booking only.

### Second Normal Form (2NF)

- All non-key attributes depend fully on the primary key.
- Separate tables are created for different entities.

Tables separated into:
- Customer
- Room
- Booking
- Payment

Example:
- Customer details are stored only in `Customer` table.
- Room details are stored only in `Room` table.

### Third Normal Form (3NF)

- No transitive dependency exists.
- Non-key attributes depend only on the primary key.

Example:
- Payment details are stored in `Payment` table instead of `Booking`.
- Customer address/email are stored in `Customer`, not in `Booking`.

### Relationships Used

- One Customer can make many Bookings (1:M)
- One Room can be reserved in many Bookings over time (1:M)
- One Booking has one Payment (1:1)

### Benefits of Normalization

- Reduced duplicate data
- Better data consistency
- Easier updates and maintenance
- Improved query structure
