# INSTA_CLONE_SQL_PROJECT
The project contains SQL queries for analyzing an Instagram-style database, covering user demographics, engagement metrics, and bot detection. Built with MySQL, it features data aggregation, multi-table joins, subqueries, and conditional filtering to extract insights on user activity and content trends.
Instagram Database Analytics & SQL Queries
An advanced SQL analytics project demonstrating complex querying, data aggregation, and performance analysis on an Instagram-style relational database. This repository serves as a comprehensive toolkit for uncovering user engagement patterns, content trends, and platform activity metrics.

🚀 Key Analytics & Business Questions Answered
User Lifecycle & Acquisition: Identifies the oldest registered accounts and determines peak registration days of the week to optimize marketing and ad campaign scheduling.

Engagement & Activity Metrics: Calculates average user posting frequency, ranks users by total photo output, and tracks active versus inactive user bases.

Content Performance: Uncovers top-performing posts by like counts, identifies the most commonly used hashtags, and tracks photo-tagging distributions.

Platform Health & Bot Detection: Employs advanced subqueries and conditional aggregates (using HAVING, LEFT JOIN, and nested subqueries) to detect anomalies like bot accounts (users liking every single photo) and silent/celebrity accounts (users with zero comments).

🛠️ Technologies & SQL Concepts Used
Database Management System: MySQL

Core SQL Operations:

Multi-table Joins (INNER JOIN, LEFT JOIN)

Data Aggregation (GROUP BY, COUNT, SUM, AVG)

Conditional Filtering (HAVING, WHERE, IS NULL)

Subqueries & Derived Tables (Nested queries for advanced metric calculations)

String & Date Functions (DATE_FORMAT, DAYNAME, ROUND)

📁 Repository Structure
Plaintext
├── queries.sql          # Complete collection of structured SQL analysis scripts
└── README.md            # Project documentation
💡 Sample Query Highlight
Here is a sample query used to identify inactive users who have never posted a photo, helping target email re-engagement campaigns:

SQL
SELECT username
FROM users
LEFT JOIN photos ON users.id = photos.user_id
WHERE photos.id IS NULL;
🚀 How to Use
Clone or download this repository to your local machine.

Import your Instagram database schema into your MySQL environment.

Open queries.sql in any SQL-compatible client (such as MySQL Workbench, DBeaver, or VS Code).

Execute the queries sequentially to analyze user behavior, engagement trends, and platform statistics.
