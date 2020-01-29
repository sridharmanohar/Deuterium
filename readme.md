## GENERAL INFO:
+ advancenalytics google drive has sheet and other info.
+ There is a kanban board in this drive, which contains stories and tasks and progress - track and update there only!
+ All other notes can be put here.


## BOOKMARKS:
+ How to integrate spring boot and aws dynamodb for developing a REST API:
    https://blogs.rayfocus.com/integrate-spring-boot-with-amazon-dynamodb/
+ DynamoDB best practices:
    https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html
+ Spring Boot as AWS Lambda:
    https://keyholesoftware.com/2018/04/26/aws-lambda-with-spring-boot/
+ AWS DynamodDB with Spring Boot:
    https://medium.com/@contactsunny/integrate-aws-dynamodb-with-spring-boot-687cfaabfaa0
    https://www.baeldung.com/spring-data-dynamodb
+ AWS Lambda (plain java) with DynamoDB:
    https://www.baeldung.com/aws-lambda-dynamodb-java

## STATUS UPDATES:
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
+ Status Updates: 29th jan 2019:
    + So far I have been able to achieve SpringBoot as an AWS Lambda service. The project is under spring-boot-lambda under my-projects.
    + And then I was also able to achieve Java as an AWS Lambda service connecting to an DynamoDB instance. This project is under java-lambda-dynamodb-v0 under my-projects.
    + I am now trying to make a SpringBoot as an AWS Lambda function using DynamoDB. The trial project is under springboot-lambda-dynamodb-v0. 
        + And to do this I am taking the help of rayfocus-tasklet.api and spring-data-dynamodb projects under my-projects, these are springboot+dynamodb projects. 
        + I am trying to figure out how to build the springboot+dynamodb as a lambda function.
        + Added some dependencies in pom.xml. Let's try and build around them and let's see how it goes!
    