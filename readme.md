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
+ **Status Update: 2nd Jan 2019:**
	+ Decided to put financial info sheets on s3 and use aws lambda to read the data and dump into a datastore on aws.
	+ Accessing google sheets needs special rules and other things, so I thought, why not use aws and use python pandas to get the job done.
	+ This approach will also serve me to know aws better.
+ **Status Update: 7th Jan 2019:**
    + Next steps are to create an aws rds postgres db
    + create a table to store balance sheet details
    + modify the python code to dump the balance sheet details into this table
    + now create a master table to hold all companies info and alter balance sheet table to have a FK relationship and modify code to dump accordingly
+ **Status Update: 8th jan 2019:**
    + Did some pricing research and it seems like if I go ahead and use aws rds (postgre), it could cost me around 15 USD p.m.
    + And, for dynamoDB, it might cost me around 5 USD p.m
    + And, If I can use S3 itself as some kind of a db, then it would cost be around 4 USD p.m, I guess.
    + So, I will be going ahead with dynamodb option.
    + Need to quickly go through the aws dynamodb best practices.
    + Need to design the database and dump data into dynamo db.
+ **Status Updates: 29th jan 2019:**
    + So far I have been able to achieve SpringBoot as an AWS Lambda service. The project is under spring-boot-lambda under my-projects.
    + And then I was also able to achieve Java as an AWS Lambda service connecting to an DynamoDB instance. This project is under java-lambda-dynamodb-v0 under my-projects.
    + I am now trying to make a SpringBoot as an AWS Lambda function using DynamoDB. The trial project is under springboot-lambda-dynamodb-v0. 
        + And to do this I am taking the help of rayfocus-tasklet.api and spring-data-dynamodb projects under my-projects, these are springboot+dynamodb projects. All these projects are on aws lambda with almost the same name as that of the project.
        + I am trying to figure out how to build the springboot+dynamodb as a lambda function.
        + Added some dependencies in pom.xml. Let's try and build around them and let's see how it goes!
+ **Status Update: 31st Jan 2019:**
    + Have put some code in place in the springboot-lambda-dynamodb-v0 and deployed it on aws, not working!.
    + Have downgraded the spring version from 2.2.0 to 1.5.9, since SpringBootServletInitialiazer and stuff that is used in LambdaHandler is not present in 2.2.0, so downgraded, it's getting called but when I call it from API, its throwing *'Missing Authenentication Token'* error.
    + Added a new test template, seeing some new errors, have to investigate:
    *org.springframework.web.util.NestedServletException: Request processing failed; nested exception is com.amazonaws.services.dynamodbv2.model.AmazonDynamoDBException: The security token included in the request is invalid. (Service: AmazonDynamoDBv2; Status Code: 400; Error Code: UnrecognizedClientException; Request ID: N6A4KP4AMFSAMKOEKAI20LC253VV4KQNSO5AEMVJF66Q9ASUAAJG)*
    + The above error was because I did not set the AWS Region where the database exists. It is mandatory to do that.
    + Finally, was able to make an insert by using the test template (but not yet with the api gateway endpoint).    
+ **Status Update: 06th Feb 2020:**
    + You create a jar for the springboot-lambda-dynamodb-v0 project by running 'mvn clean package shade:shade' command from command-line. Then just upload the jar into the aws lambda web console.
    + I wanted to see why am I not able to trigger the code with api endpoint (keep getting missing authentication token), so I created the api with 2 resources i.e. /languages and /experts and two GET methods within them. I have these two resources in my controller (i.e. LanguageResource.java) and the calls went fine, I got the response back.
    + This means, the problem is only with POST.
    + So, I modified the RequestMethod type from POST to GET in my code for /save and then created a resource by the name /save and a GET underneath it and then deployed it and clicked on the endpoint and that's it. Perfect. Went fine.
    + So, the issue was with what was being sent in the request (porbably) for POST from the API Endpoint. Not sure though. But, I am, able to make inserts into the dynamod db by using GET.
    + So, I think the feasibility POC is over. Most of the code for this project i.e. springboot-lambda-dynamodb-v0 is taken from spring-boot-lambda - this project is also on aws lambda by the same name as that of the project.
    + Now, I am planning to create an almost working prototype of atleast one rest api which will fetch the details that I want to in deuterium.
    + I have deleted the spring-data-dynamodb (a baeldung) projectfrom my repo, not very useful and also somewhat errorprone.