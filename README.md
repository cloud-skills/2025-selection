# Korea national selection match

### Day1 - Solution Architecture
- The binary provided is test to be compatible with AmazonLinux2023 x86 and implemented by FastAPI that works asynchronously.
- There is no load-test during the test project.
- There is no database fail-over test during grading.
- Database connection latency doesn't matter, but the API has to respond within 10 seconds.
- You will be given 4.5 hours for the test project.

### Day2 - System Operation
- System Operation test project is used instead of Small Challenge.
- The Load-test will begin 1 hour after the start of the competition.
- You must not delete the created IAM users before the start of the competition.
- DocumentDB instance type doesn't impact on your score.
- Dashboard : http://dashboard.t1kc2502korea.com
- Evaluation scripts may be executed at any time, including during breaks (e.g., lunch hours).
- Chaos attacks may occur at any time without prior notice.

### Day3 - Small Challenge
- Small Challenge test project is used instead of System Operation.
- You will be given 2.5 hours for the test project.
- For the question3 - Secure the objects, you have to set the description of the CloudFront distribution as "dragons-very-security-website"
- For the question4 - Shout the password, you have to set the description of the CloudFront distribution as "unicorn-company"
- For the MLOps - Create only one Notebook file and instance.
- For the MLOps - If any part of your code loads data from S3, the Notebook file must also include logic that retrieves the same data through the Feature Store.
