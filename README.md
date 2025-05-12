# Lambda Function: [notifysummary]
# Azure Function: [notifysummary]

## Overview

This function, named `[notifysummary]`, serves the purpose of sending email notification based on trigger from Queue (SQS/Storage Queue)once the summary is generated. It is built using Javascript running on Node JS runtime environment and deployed within the AWS Lambda/Azure Function App environment.

## Functionality

This function performs the following actions:

1.  Send Email notification using Send Grid based on SQS/Storage Queue Invocation respectively for AWS Lambda/Azure Function.

## Deployment

This function can be deployed using various methods, including:

* **AWS/Azure Management Console:** Manual creation and configuration through the AWS/Azure web interface.
* **Infrastructure as Code (IaC) tools (e.g., Terraform, Pulumi):** Third-party tools for managing cloud infrastructure.

**Deployment Package:**

The function code and its dependencies (if any) are packaged into a ZIP file named `notifysummary.zip` (or a similar name depending on your deployment method).

## Configuration

The following environment variables can be configured for this Lambda function:

* `[SENDGRID_API_KEY]`: Send Grid API Key
* `[TO_EMAIL]`: To email address
* `[FROM_EMAIL]` : From Email address
* `[REGION]` : AWS Region Name
* `[AZQUEUE_NAME]` : Azure Storage Queue Name
* `[AZQUEUE_URL]` : Azure Storage Queue URL

These variables can be set through the AWS/Azure Management Console, AWS CLI, or your chosen IaC tool.

## Permissions

The execution role associated with this Lambda function (`arn:aws:iam::[your_account_id]:role/[your_lambda_execution_role]`) has the following AWS managed policies and/or custom permissions attached:

* `AWSLambdaBasicExecutionRole`: Provides basic permissions for a Lambda function to write logs to CloudWatch Logs.
* `AmazonSQSFullAccess`: Provides Lambda function to add/remove messages into SQS

## Input and Output

**Input:**

The structure of the input event passed to this Lambda function depends on the event source that triggers it. 

**Output:**

The output of the Lambda function depends on how it is invoked and integrated with other services. Common output formats include:

* **API Gateway Integration:** A JSON object representing the HTTP response (status code, headers, body).
    ```json
    {
      "statusCode": 200,
      "headers": {
        "Content-Type": "application/json"
      },
      "body": "{\"message\": \"Email sent successfully!\"}"
    }
    ```

## Logging and Monitoring

This Lambda function utilizes AWS CloudWatch Logs for logging. You can find detailed logs of the function's execution in the CloudWatch Logs service under the log group `/aws/lambda/[YourFunctionName]`.
For Azure, you can view logs in Application Insights.
