# Internal reporting for a news website
In this project a mock PostgreSQL database **news** for a fictional news website is set up (details in usage chapter below). The provided Python script **newsdata_internalReporting.py** uses the psycopg2 library to query the database and produce a report that answers the following three questions:

1) What are the most popular three articles of all time?

2) Who are the most popular article authors of all time?

3) On which days did more than 1% of requests lead to errors?

### Usage
First you need to create the PostgreSQL database **news**:
- Download the following [script](https://d17h27t6h515a5.cloudfront.net/topher/2016/August/57b5f748_newsdata/newsdata.zip), which will enable you to create the database and populate 3 tables with dummy data
- To do so run `psql -d news -f newsdata.sql`

Now you can run the Python code **newsdata_internalReporting.py** by using following command in the terminal:

`python newsdata_internalReporting.py`

This will print out the results to the open questions in your terminal.

### Program structure
- Line 13 imports the library **psycopg2** which is needed to connect to a PostgreSQL Database
- Line 17-24 is a function **create_internal_report** that takes a SQL query as an input, connects to the database, runs the query and returns the results in a list
- Line 27-31 is a function **print_internal_report** that takes the list output from the previous function **create_internal_report** and prints the results in a readable manner ready to be inserted in an email e.g.
- Line 37-105 are 3 SQL queries (1 for each question) that are used as an input for the function **create_internal_report** described above
- Line 108-110 runs the function **create_internal_report** with each query and returns the reporting results
- Line 113-118 prints the results to all questions using the **print_internal_report** function

### Program output
**1) What are the most popular three articles of all time?**

Candidate is jerk, alleges rival - 338647 views

Bears love berries, alleges bear - 253801 views

Bad things gone, say good people - 170098 views

**2) Who are the most popular article authors of all time?**

Ursula La Multa - 507594 views

Rudolf von Treppenwitz - 423457 views

Anonymous Contributor - 170098 views

Markoff Chaney - 84557 views

**3) On which days did more than 1% of requests lead to errors?**

17 Jul 2016 - 2.26% errors
