# Tests

The workflow is as follows:

A new AWS account is created through AWS Organizations (or Control Tower).

Upon successful account creation, AWS Organizations emits a CreateAccountResult event.

Amazon EventBridge is configured to listen for this account creation event.

When the event is detected, EventBridge triggers an automation workflow.

The automation invokes a Lambda function running in the centralized IAM / core account.

The Lambda function retrieves the newly created AWS account ID from the event payload.

Using the AWS Identity Center (SSO Admin) APIs, the Lambda assigns one or more predefined permission sets to the new account.

Permission sets are assigned to Identity Center groups, not individual users.

The account appears in AWS Identity Center with the appropriate access already configured.
