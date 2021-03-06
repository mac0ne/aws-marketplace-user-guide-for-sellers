# Subscription Notifications<a name="subscription-notification"></a>

 To receive notifications, you subscribe to the AWS Marketplace SNS topic provided to you during product creation\. The topic provides notifications about changes to customers’ subscription and entitlement statuses\. This enables you to know when to provide and revoke access for specific customers\. 

## Subscribing an SQS Queue to the SNS Topic<a name="subscribing-an-sqs-queue-to-the-sns-topic"></a>

 We recommend subscribing an Amazon SQS queue to the provided SNS topic\. Detailed instructions on creating an SQS queue can be found at [Tutorial: Creating an Amazon SQS Queue](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-create-queue.html)\. Instructions for subscribing the queue to the provided topic can be found at [Tutorial: Subscribing an Amazon SQS Queue to an Amazon SNS Topic](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-subscribe-queue-sns-topic.html)\. 

## Polling the SQS Queue for Notifications<a name="polling-the-sqs-for-notifications"></a>

 Finally, you need to define a service that continually polls the queue, looking for messages, and handling them accordingly\. 

 Example of polling the SQS queue for notifications 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-polling-sqs-queue.png)

**Note**  
As a SaaS subscriptions provider, you must handle four actions:  
`subscribe-success`
`subscribe-fail`
`unsubscribe-pending`
`unsubscribe-success`
 As a SaaS contracts provider, you will only get an `entitlement-updated` SNS notification to let you know that a customer’s contract has been created, updated, renewed, or expired\. 

## Updating SaaS Products<a name="updating-saas-products"></a>

After your product is on AWS Marketplace, you are responsible for keeping the pricing and product information up to date\.

**To make changes to your SaaS product**

1. Sign in the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/)\.

1. From the **Products** tab, choose **SaaS**\.

1. On the **SaaS products** page, you'll find your list of **Current products**\. Choose the product and submit your updated information\.