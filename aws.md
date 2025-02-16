# AWS

## Contents

- [AWS CLI Reference](#aws-cli-reference)
- [Cold Start Lambda](#cold-start-lambda)

### AWS CLI Reference

The AWS CLI is a powerful tool for interacting with AWS resources straight from your terminal. The official reference guide highlights all the use cases with examples to build from.

- [AWS CLI Command Reference](https://awscli.amazonaws.com/v2/documentation/api/latest/index.html)

### Cold Start Lambda

You can force a cold start by uploading new code to the Lambda. In some cases it can be useful to download the exiting Lambda code and immediately reupload the zip. For example, in the event that the Lambda is still warm during a deployment and you want to immediately see the latest changes.
