Instagram Clone Database Analytics & Schema
An advanced relational database management and SQL analytics project modeling an Instagram-style social media platform. This repository is structured to demonstrate robust database design, DDL schema creation, and complex analytical querying to uncover deep user engagement patterns, platform health metrics, and content trends.

📁 Repository Structure
14.Instagram Clone Database.sql — Database schema definition, table creation, constraints, and seed data setup.

15.Instagram Clone Database - Challenges.sql — Comprehensive suite of analytical SQL queries and business insights.

README.md — Project documentation.

🏗️ Database Schema Overview (14.Instagram Clone Database.sql)
The underlying database architecture is built using relational modeling principles to support core social media functionalities across multiple normalized tables:

users: Stores user profile information, unique usernames, and account creation timestamps.

photos: Tracks uploaded media content, linking each photo to its owner (user_id) along with image URLs and creation timestamps.

comments: Manages textual feedback left by users on specific photos, recording the comment body, author, and timestamp.

likes: Records user interactions via a composite primary/foreign key structure ensuring a user can like a specific photo only once.

follows: Captures directional user-to-user relationships (followers and followings) to map social graphs.

tags: Stores unique hashtag keywords utilized across posts.

photo_tags: A junction table resolving the many-to-many relationship between photos and tags.

🚀 Key Analytics & Business Questions Answered (15.Instagram Clone Database - Challenges.sql)
The analytics script addresses real-world product and marketing challenges faced by digital platforms:

1. User Lifecycle & Acquisition
Oldest Account Discovery: Identifies the foundation users who have been registered the longest to evaluate early adopter retention.

Registration Day Analysis: Determines peak days of the week for user sign-ups using date-formatting functions (DATE_FORMAT, DAYNAME) to optimize future ad campaign scheduling.

2. Engagement & Activity Metrics
Posting Frequency & Averages: Calculates the platform-wide average posting rate per user (TOTAL PHOTOS / TOTAL USERS) using subqueries and rounding functions.

User Leaderboards: Ranks active users by total photo output to identify top creators.

Active vs. Inactive Segmentation: Pinpoints dormant users who have never posted a photo using LEFT JOIN and IS NULL filters to target email re-engagement campaigns.

3. Content Performance
Contest Winner Identification: Evaluates total like counts per photo via multi-table joins (users, photos, likes) to determine viral posts and contest winners.

Hashtag Popularity Tracking: Aggregates tag frequencies using joins across tags and photo_tags to uncover trending topics and content themes.

4. Platform Health & Bot Detection
Bot Identification: Employs advanced nested subqueries and HAVING clauses to isolate automated bot accounts that have liked every single photo on the platform.

Celebrity/Silent Account Detection: Tracks users with zero comments or zero engagement interactions.

Platform Distribution Metrics: Computes proportional percentages of edge-case accounts (e.g., non-commenters vs. active commenters) to assess overall platform health.

🛠️ Technical Concepts & SQL Skills Demonstrated
DDL & Constraints: Primary keys, foreign key constraints, composite keys, and cascade operations.

Advanced Joins: Complex multi-table inner and left joins (INNER JOIN, LEFT JOIN).

Aggregation & Grouping: GROUP BY, HAVING, COUNT, SUM, AVG, and DISTINCT.

Subqueries & Derived Tables: Nested queries and inline view aliases for multi-layered metric calculations.

String & Date Manipulation: DATE_FORMAT(), DAYNAME(), and ROUND().

💡 Highlighted SQL Snippet
Below is an example query from the analytics script used to identify potential bot accounts that have liked every single photo on the platform:

SQL
SELECT users.id, username, COUNT(users.id) AS total_likes_by_user
FROM users
JOIN likes ON users.id = likes.user_id
GROUP BY users.id
HAVING total_likes_by_user = (SELECT COUNT(*) FROM photos);
🚀 How to Run the Project
Clone the Repository:

Bash
git clone <your-repository-url>
Set Up the Database:

Open your preferred MySQL client (e.g., MySQL Workbench, DBeaver, or VS Code SQL extension).

Execute 14.Instagram Clone Database.sql to create the schema, tables, and populate them with sample data.

Run Analytics:

Open and execute 15.Instagram Clone Database - Challenges.sql sequentially to review the business insights, user behavior metrics, and bot detection queries.
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
