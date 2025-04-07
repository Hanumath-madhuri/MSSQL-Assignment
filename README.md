# MSSQL-Assignment
README.md

📘 Product Search Optimization - DBA Analysis Report
📌 Scenario
As part of the DBA team managing an e-commerce platform, a developer reported that the **product search feature is running slow**. The underlying data is stored in the `Products` table with over **10,000 rows**.
🗄️ Table Structure
--sql
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(100),
    Category VARCHAR(50),
    Price DECIMAL(10,2),
    InStock INT,
    CreatedAt DATETIME
);

Assumptions:
•	The search query likely filters by ProductName, Category, Price, or InStock.
•	CreatedAt is used for sorting or filtering recent products.
•	ProductID is the clustered primary key.
•	Queries are read-heavy and involve filtering and ordering.

Approach:
Step 1: Identify Common Queries

Typical search patterns:
•	Search products in stock by name or category.
•	Sort by price or filter by price range.
•	View new arrivals (last N days).

Step 2: Write & Analyze SQL Queries

Optimization Suggestions
•	Indexes are Recommended for better query optimization.
•	Index usage should be verified using execution plans and actual query patterns.
•	indexes support filtering (WHERE) and sorting/grouping operations efficiently.

Execution Plan Check:
•	This reveal estimated I/O cost, scans/seeks, and missing indexes if any.
•	Execution plan shows how SQL Server processes a query, which helps identify potential bottlenecks like missing indexes, table scans, or expensive operations.
•	It Shows the plan without running the query.

Real-World Handling Strategy:
•	Capture slow queries using Query Store or Extended Events.
•	Analyze execution plans for missing indexes, scans, and key lookups.
•	Collaborate with developers to review query logic and pagination.
•	Add appropriate non-clustered indexes and monitor performance.
•	Implement caching (e.g., Redis, DAX for NoSQL) if read patterns are repetitive.
•	Partitioning or archiving older data if growth impacts performance.
•	Monitor performance metrics regularly (CPU, I/O, wait stats).

