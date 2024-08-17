**Project: Little Lemon Analysis and Sales Report - Database Integration**

### Software and Packages Utilized:

- Python
- MySQL Server
- Jupyter Notebook
- MySQL Connector/Python API

### Project Overview:

Little Lemon is a family-owned Mediterranean restaurant developing a Python-based application designed to interface with a MySQL database. This integration will enable the storage and management of booking, menu, and order data across dedicated tables.

The restaurant owner aims to leverage this stored data to make data-driven decisions to optimize revenue. One of the primary objectives is to establish and maintain a robust database.

### Database Setup Process:

1. **Establish a Connection:**
   - Initiate a new Jupyter Notebook session and import the MySQL Connector/Python API to create a connection between Python and the MySQL database.

2. **Create a Cursor:**
   - Upon successful connection, instantiate a cursor object to facilitate communication with the MySQL database.

3. **Database Creation:**
   - Utilize the established connection and cursor to create a new database, `little_lemon_db`, and set it as the active database.

4. **Table Creation and Data Insertion:**
   - Develop and populate the following tables within the `little_lemon_db` database: `MenuItems`, `Menu`, `Bookings`, `Orders`, and `Employees`.

5. **Stored Procedures Implementation and Querying:**
   - Establish a connection pool using `MySQLConnectionPool`, and retrieve connections to implement stored procedures for the following tasks:
     - **`PeakHours` Procedure:** Identifies peak hours based on booking data.
     - **`GuestStatus` Procedure:** Outputs guest order statuses based on employee assignments.

### Tasks and Implementation Steps:

**Task 1: Establish Connection Pool**

- **Step 1:** Import `MySQLConnectionPool`.
- **Step 2:** Import `Error` handling class.
- **Step 3:** Define a connection pool, `pool_a`, with two connections, employing a try-except block for error management.
- **Step 4:** Retrieve a connection from `pool_a` and create a cursor object for database interaction.

**Task 2: Implement `PeakHours` Stored Procedure**

- **Step 1:** Draft a SQL `CREATE PROCEDURE` query to define `PeakHours` using `HOUR`, `COUNT`, `GROUP BY`, and `ORDER BY` clauses.
- **Step 2:** Execute the stored procedure query using the cursor's `execute` method.
- **Step 3:** Invoke the stored procedure using `callproc`.
- **Step 4:** Fetch the results into a `dataset` variable, extract column names, and output the sorted data.

**Task 3: Implement `GuestStatus` Stored Procedure**

- **Step 1:** Draft a SQL `CREATE PROCEDURE` query for `GuestStatus`.
- **Step 2:** Use `CONCAT` to merge guest names and `CASE` to implement role-based order statuses.
- **Step 3:** Perform a `LEFT JOIN` between `Bookings` and `Employees`.
- **Step 4:** Execute the query, call the stored procedure, fetch the results, and print them.

**Task 4: Create Connection Pool for Concurrent Bookings**

- **Step 1:** Import `MySQLConnectionPool` and `Error`.
- **Step 2:** Define database configurations and establish a connection pool (`pool_b`) with two connections.
- **Step 3:** Use a try-except block for error handling.

**Task 5: Insert Guest Bookings Simultaneously**

- **Step 1:** Utilize connections from `pool_b` to insert booking data for three guests.
- **Step 2:** Handle the scenario where a third connection cannot be returned to the pool, using a try-except block to capture `PoolError`.

**Task 6: Generate a Managerial Report**

- **Step 1:** Report details include the manager's name, employee with the highest salary, guest booking count between 18:00 and 20:00, and guests awaiting seating, sorted by `BookingSlot`.

**Task 7: Implement `BasicSalesReport` Stored Procedure**

- **Step 1:** Create a stored procedure to return total sales, average sale, minimum bill, and maximum bill.

**Task 8: Display Upcoming Bookings**

- **Step 1:** Retrieve the next three bookings from the `Bookings` table to display on the kitchen screen.
- **Step 2:** Return the connection to the pool after processing.

**Output Format:**
- `[BookingSlot]`
- `[Guest_name]`
- `[Assigned to: Employee Name [Employee Role]]`

Finally, print the sorted data and ensure the connection is closed to return it to the pool.
