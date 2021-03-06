# 4. Create the Backend Resources

For this sample you will need backend AWS resources that support the skill. Using the Alexa Skill ID from the previous step, you will create a CloudFormation Stack using a provided template that generates the following in your AWS account:

- An IAM Lambda Execution Role with a restrictive Policy
- An AWS Lambda Function with Triggers configured for Alexa using the restrictive Role
- A Simple Queue Service (SQS) Queue for messages to our device 

## Apply the CloudFormation Template

Access the AWS CloudFormation console in your preferred region and load a template file to provision backend resources.

1. Login to the AWS Console for CloudFormation at [https://console.aws.amazon.com/cloudformation/home](https://console.aws.amazon.com/cloudformation/home) (then select the region that is most appropriate for your smart home locale of choice, eg. for North America choose *us-east-1*, for Europe and India choose *eu-west-1* and for Far East choose *us-west-1*).
2. Click **Create stack** and select **With new resources (standard)**.
3. Select **Template is ready** and **Upload a template file**. Select the `self.multi.template.json` (US) or the `self.eu.multi.template.json` (EU) file. 
4. Click **Next**.
5. For the **Stack name** on the *Stack Details* page, enter `skill-sample-python-multi`.
6. In the **AlexaSkillId** field of the *Parameters*, enter the Alexa Skill ID of the previously created skill stored in the **[Alexa Skill Application ID]** section of the `setup.txt` file.
7. Click the **Next** button.
8. On the *Options* page, no changes are needed and you can just click the **Next** button.
9. On the *Review* page, check the **I acknowledge that AWS CloudFormation might create IAM resources.** check box and then click the **Create stack** button.

> The status of the stack should start as `CREATE_IN_PROGRESS` and complete after a couple of minutes. You can view the status of the stack creation on the CloudFormation console.

## Collect the CloudFormation Stack Outputs

After the stack completes, collect the created resource identifiers.

1. When the *skill-sample-python-multi* stack is created, you will see its *Status* reported as `CREATE_COMPLETE`.
2. From the *Outputs* tab of the stack, collect value of the `PagerFunctionLambdaArn` key and store it into the **[AWS Lambda ARN]** section of the `setup.txt` file in your working directory. It will look something like the following: `arn:aws:lambda:region:XXXXXXXXXXXX:function:skill-sample-python-multi`.
3. While in the *Outputs* tab, also collect the `PagerSqsQueueUrl` value and store it in the **[Amazon SQS Queue Url]** section of the `setup.txt` file.

	```
	[AWS Lambda ARN]
	arn:aws:lambda:region:XXXXXXXXXXXX:function:skill-sample-python-multi

	[Amazon SQS Queue Url]
	https://sqs.region.amazonaws.com/XXXXXXXXXXXX/PagerEventQueue
	```


## Checkpoint
In your AWS environment, you should now have the following resources available to you:

- An IAM Lambda Execution Role with a restrictive Policy
- An AWS Lambda Function with Triggers configured for Alexa using the restrictive Role
- A Simple Queue Service (SQS) Queue for messages to our device

You should also have saved the Lambda ARN and SQS Queue URL to be used later during configuration.

Next to Step [5. Create a Security Profile](create-a-security-profile.md)

___
Return to the [Instructions](README.md)