Logs Analysis:

The first project in Udacity's full stack web development nanodegree program.

Project Overview
The project requires students to create and use SQL queries that would fetch results from a large database of a news website.The objective of this project is to extend the student's SQL database skills. The code requirements suggest the use of only one single query to answer each request. The answer code presented here does not change the original database but utilizes views to answer the third query.

Requirements
Python 3 - The code uses ver 3.6.4
Vagrant - A virtual environment builder and manager
VirtualBox - An open source virtualiztion product.


How to access the project?
Follow the steps below to access the code of this project:

If you don't already have the latest version of python download it from the link in requirements.
Download and install Vagrant and VirtualBox.
Download this Udacity folder with preconfigured vagrant settings.
Download this database.
Navigate to the Udacity folder in your bash interface and inside that cd into the vagrant folder.
Open Git Bash and launch the virtual machine withvagrant up
Once Vagrant installs necessary files use vagrant ssh to continue.
The command line will now start with vagrant. Here cd into the /vagrant folder.
Unpack the database folder contents downloaded above over here. You can also copy the contents of this repository here.
To load the database type psql -d news -f newsdata.sql
To run the database type psql -d news
You must run the commands from the Create views section here to run the python program successfully.
Use command python3 reporting.py to run the python program that fetches query results.

Create Views
Views were created to answer the third query in the project with the purpose of leaving the original database unchanged. They also helped break the question down into comprehensible portions.

The first view code is as follows:

CREATE VIEW total_errors AS SELECT cast(time as date) as error_date,count(*) as count_errors
FROM log WHERE status <> '200 OK'
GROUP BY error_date
ORDER BY count_errors desc limit 3;

The second view code is as follows:

CREATE VIEW total_requests AS SELECT cast(time as date) as request_date,count(*) as total
FROM log 
GROUP BY request_date;


Troubleshooting
If your command prompt does not start with vagrant after typing vagrant ssh then please try the winpty vagrant ssh on your Windows system.





