# mystery-package-tracking---SQL-journal-day-3
day 3 of learning SQL - solving the mystery packages
# Mystery Package Tracking: Rubber Duck

## Introduction
In this project, I tracked a package containing a **Rubber Duck** from its pickup to its drop-off location. The task was to use SQL queries on a SQLite database to track the package's journey and verify its delivery.

---

## Process

### Step 1: Finding Relevant Packages
To find all packages related to "duck" or "quack," I ran the following query:

```sql
SELECT * FROM packages
WHERE contents LIKE '%duck%' OR contents LIKE '%quack%';

Result:
This query returned a list of packages containing a Rubber Duck. The relevant entry is package ID 5098, which contains a Duck debugger.

Step 2: Check Package Scan History
Next, I traced the package's scan history to find where it was picked up and dropped off. I ran this query:


SELECT * FROM scans
WHERE package_id = 5098
ORDER BY timestamp;
Result:
The scans revealed the following details:


Scan ID	Driver ID	Package ID	Address ID	Action	Timestamp
30123	10	5098	50	Pick	2023-10-24 08:40:16.246648
30140	10	5098	348	Drop	2023-10-24 10:08:55.610754
Step 3: Trace the Drop-off Location
To find the location where the package was dropped off, I ran the following query:


SELECT * FROM addresses
WHERE id = 348;

Result:
The drop-off location is 7 Humboldt Place, which is classified as a Police Station.

Conclusion
The Rubber Duck package was picked up at address ID 50 and dropped off at 7 Humboldt Place (Police Station).

Queries Used

-- Step 1: Find all packages related to 'duck'
SELECT * FROM packages
WHERE contents LIKE '%duck%' OR contents LIKE '%quack%';

-- Step 2: Find package scan history for package ID 5098
SELECT * FROM scans
WHERE package_id = 5098
ORDER BY timestamp;

-- Step 3: Find the drop-off location for the package
SELECT * FROM addresses
WHERE id = 348;
