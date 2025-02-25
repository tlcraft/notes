# AWS

## Contents

- [AWS CLI Reference](#aws-cli-reference)
- [DynamoDB CLI](#dynamodb-cli)
- [Cold Start Lambda](#cold-start-lambda)
- [DynamoDB read and write operations](#dynamodb-read-and-write-operations)
- [Stress Tool](#stress-tool)

### AWS CLI Reference

The AWS CLI is a powerful tool for interacting with AWS resources straight from your terminal. The official reference guide highlights all the use cases with examples to build from.

- [AWS CLI Command Reference](https://awscli.amazonaws.com/v2/documentation/api/latest/index.html)

### DynamoDB CLI

The AWS CLI can be used to interact with DynamoDB. You can use separate files to help compose your queries and reference those in the commands. Responses can be saved to files as well.

- [AWS CLI DynamoDB Query Example](https://medium.com/@corymaklin/tutorial-aws-part-5-the-basics-of-dynamo-db-amazons-non-relational-database-9be0cf500e6e)
- [query](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/dynamodb/query.html)
- [Export a DynamoDB table as CSV through AWS CLI](https://stackoverflow.com/questions/33357821/export-a-dynamodb-table-as-csv-through-aws-cli-without-using-pipeline)

### Cold Start Lambda

You can force a cold start by uploading new code to the Lambda. In some cases it can be useful to download the exiting Lambda code and immediately reupload the zip. For example, in the event that the Lambda is still warm during a deployment and you want to immediately see the latest changes.

### DynamoDB read and write operations

DynamoDB is a NoSQL database with various read and write methods. DynamoDB uses read and write capacity units when performing operations. These can be calculated based on your needs. The following pages describe the calculations.

- [Read capacity units and write capacity units](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/provisioned-capacity-mode.html#read-write-capacity-units)
- [DynamoDB read and write operations](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/read-write-operations.html)

### Stress Tool

AWS has a tool which can stress Linux EC2 instances if needed. Log in, install and run the `stress` command. The Fault Injection Service can also be used to stress CPUs.

- [How to quickly stress test CPU on Amazon Linux](https://gregsnotes.medium.com/how-to-quickly-stress-test-cpu-on-amazon-linux-7fc49c473334)
- [Tutorial: Run CPU stress on an instance using AWS FIS](https://docs.aws.amazon.com/fis/latest/userguide/fis-tutorial-run-cpu-stress.html)
