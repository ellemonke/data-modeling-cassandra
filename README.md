## NoSQL (Non-relational) Data Modeling with Apache Cassandra
A sample company, Sparkify, has provided daily logs of song plays on their music streaming app in the folder ['event_data'](event_data/). The data is a sample subset of real data from the [Million Song Dataset](https://labrosa.ee.columbia.edu/millionsong/).

The goal of the project is to create an ETL pipeline that denormalizes the data in Apache Cassandra and directly answers ad-hoc data analysis queries. All steps are completed in the Jupyter notebook ['etl_cassandra.ipynb'](etl_cassandra.ipynb).

Sample data in CSV format:
<img src="images/image_event_datafile_new.jpg" />

<hr>

### Project Steps

**Part 1.** Process all CSV files into one temporary staging file called 'event_datafile_new.csv'.

**Part 2.** Create a connection to a local instance of Cassandra on your machine and create a keyspace to perform your queries.

**Part 3.** Using SQL, write your ad hoc queries in the following steps:

1. First, consider the `SELECT` query you will be writing for analysis and how the data may be partitioned onto unique nodes and somewhat evenly distributed. A good place to consider partitioning data is by looking in the `WHERE` clause.

2. Write `CREATE TABLE` and `INSERT INTO` statements data based on the analysis query. The `PRIMARY KEY` is first defined by the **partition key** where one or more columns represent your data partitions. Optionally, **clustering columns** may be included at the end of the `PRIMARY KEY` to logically order the data in the partitions for faster retrieval.

3. Then run the `SELECT` query to test and find your results. 

**Sample Queries:**  
- Find the artist, song title and song's length in the music app history that was heard during sessionId = 338, and itemInSession = 4.
- Find the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182.
- Find every user name (first and last) in my music app history who listened to the song "All Hands Against His Own".

**Part 4.** Drop the tables and close the Cassandra cluster connection. 