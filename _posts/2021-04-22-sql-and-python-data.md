---
layout: post
title: SQL and Python
date: 2021-04-21 20:43:47.000000000 +11:00
type: post
permalink: "/sql-and-python-data/"
---

## Notes on using data from Python (like a list of values) with SQL databases and tables (also in Python).

Examples below assume ysing the MySQL Python connector.

Basic setup for connecting to the SQL database in using the MySQL connector:

    import mysql.connector   
    import json

    cnx = mysql.connector.connect(user='yourtableuser',                                                                   
                                  password='yourpassword!',
                                  host='localhost',
                                  database='yourdatabase')

    cur = cnx.cursor()
    
    #check if connection works
    cur.execute("""select * from yourtable""")
    
    res = cur.fetchall() #returns list of tuples, each tuple is a row



Once connected there are a few ways we may want to use the data in Python with our SQL database.


Inserting multiple rows into a database from a dataset in Python using executemany, MySQL expects each row to be a tuple:

    example_list_of_tuples = [('1','Keith','20'),('2','Alex','22')]
    cur.executemany("INSERT INTO yourtable (id, name, age) VALUES (%s, %s, %i)", example_list_of_tuples)


Updating multiple rows in a database, data structure order must match column order:

    example_list_of_tuples = [('Keith','20','1'),('Alex','22','2')]
    cur.executemany("UPDATE yourtable SET name=%s, age=%i WHERE id=%s", example_list_of_tuples)


Selecting rows in a database based on criteria from Python using execute (cannot use executemany for SELECT statements):

    list_of_criteria = [('1'),('2')]
    format_strings = ','.join(['%s'] * len(list_of_criteria))
    cur.execute("SELECT * FROM yourtable WHERE id IN (%s)" % format_strings, tuple(id))


And remember to commit all your changes to finish:

    cnx.commit()