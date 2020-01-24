+ advancenalytics google drive has sheet and other info.
+ There is a kanban board in this drive, which contains stories and tasks and progress - track and update there only!
+ All other notes can be put here.

+ How to create a postgres aws rds instance and what details to enter:
https://aws.amazon.com/getting-started/tutorials/create-connect-postgresql-db/

+ How to connect to an aws rds postgres instace using pgadmin and psql:
https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ConnectToPostgreSQLInstance.html

+ How to integrate spring boot and aws dynamodb for developing a REST API:
https://blogs.rayfocus.com/integrate-spring-boot-with-amazon-dynamodb/

+ How to integrate spring boot and aws dynamodb (running locally):
https://www.baeldung.com/spring-data-dynamodb

+ DynamoDB best practices:
https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html


+ Status Update: 2nd Jan 2019:
	+ Decided to put financial info sheets on s3 and use aws lambda to read the data and dump into a datastore on aws.
	+ Accessing google sheets needs special rules and other things, so I thought, why not use aws and use python pandas to get the job done.
	+ This approach will also serve me to know aws better.

+ Status Update: 7th Jan 2019:
    + Next steps are to create an aws rds postgres db
    + create a table to store balance sheet details
    + modify the python code to dump the balance sheet details into this table
    + now create a master table to hold all companies info and alter balance sheet table to have a FK relationship and modify code to dump accordingly

+ Status Update: 8th jan 2019:
    + Did some pricing research and it seems like if I go ahead and use aws rds (postgre), it could cost me around 15 USD p.m.
    + And, for dynamoDB, it might cost me around 5 USD p.m
    + And, If I can use S3 itself as some kind of a db, then it would cost be around 4 USD p.m, I guess.
    + So, I will be going ahead with dynamodb option.
    + Need to quickly go through the aws dynamodb best practices.
    + Need to design the database and dump data into dynamo db.