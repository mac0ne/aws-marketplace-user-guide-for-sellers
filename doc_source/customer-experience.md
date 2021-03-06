# Customer Experience<a name="customer-experience"></a>

 The steps that the customer follows with SaaS subscriptions and SaaS contracts are slightly different\. 

 **SaaS Subscriptions** 

 Under the SaaS subscriptions model, customers subscribe to your software on the AWS Marketplace website and pay only for what they use\. Before subscribing, they see the prices for the dimensions that they use in your software\. The following image shows an example of pay\-as\-you\-go prices\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-customer-experience-subscription.png)

 **SaaS Contracts** 

 Under the SaaS contracts model, customers purchase quantities of usage for a contract duration on the AWS Marketplace website\. Depending on your pricing, the customer can select speciﬁc quantities of varying dimensions or pick from a set of options\. The following image shows an example of a duration selection\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-customer-experience-contract.png)

## Automatic Renewals<a name="automatic-renewals"></a>

 When a customer purchases your product through AWS Marketplace using SaaS contracts, they can agree to automatic renewal of the contract terms\. The customer continues to pay for the entitlements every month or for 1, 2, or 3 years\. The customer always has the option to modify the renewal settings\. They can cancel the renewal or renew the contract diﬀerent quantities and durations\. 

## Upgrades<a name="upgrades"></a>

 Customers can upgrade a contract to one of a higher value except for longer durations\. For example, they can upgrade to higher quantities or higher\-value entitlements\. Customers are given a prorated credit for their existing contract\. Customers can't decrease the size of their existing contract\. They can only decrease the size at renewal, or cancel their renewal\. 

 **Example**: A customer purchased a 1\-month contract on April 1, 2018, for one unit priced at $100\. Ten days into the contract, the customer requires more units\. The customer expands the current contract to four units \(adding three more on April 11, 2018\)\. The expiration date of the contract remains the same: May 1, 2018\. 

 The price for the upgrade is calculated on a prorated basis: 

 Used: 10 days out of 30 days in the month of April, used one unit priced at $100/unit/month = \(10/30\) x $100 x 1 = $33\.33 

 Will use: 20 days remaining in a contract for four units priced at $100/unit/month = \(20/30\) x $100 x 4 = $266\.66 

 Because the customer already paid $100 when you purchased the original contract for one unit on April 1, 2018, the price to upgrade to four units on April 11, 2018, is $200, calculated from \($266\.66 \+ $33\.33\- $100\)\. 

 Entitlements are veriﬁed by your SaaS product, which makes calls to the AWS Marketplace Contract Service\. 

## Security and Ordering<a name="security-and-ordering"></a>

 As a seller, it’s your responsibility to trust only customer identiﬁers that are immediately returned from AWS or those that your system has signed\. We recommend that you resolve the registration token immediately because it expires after 1 hour\. After you resolve the registration token, store the customer identiﬁer as a signed attribute on the customer’s browser session until the registration is complete\. 

## When a SaaS Subscription or SaaS Contract Ends<a name="disable-customers-when-a-saas-subscription-or-saas-contract-ends"></a>

 A customer can unsubscribe from your SaaS subscription product through the AWS Management Console\. A SaaS contracts product has a contract expiry\. When a customer unsubscribes or if their contract ends, the following events occur: 

1.  Your SaaS product is sent an `unsubscribe-pending` notiﬁcation through the Amazon SNS topic for that customer\. For a SaaS contract, you also receive an `entitlement-updated` notification indicating their entitlement has changed, and the AWS Marketplace Entitlement Service returns an empty response\. 

1.  You have one hour to meter any remaining usage for the customer\. 

1.  After this hour, you receive an `unsubscribe-success` notiﬁcation\. At this point, you can no longer send metering records for this customer\. 

 It’s up to you to decide how you want to disable functionality in your SaaS product for unsubscribed customers\. For example, your product might complete the customer's existing work, but prevent them from creating work\. You might want to display a message to the customer that their usage has been disabled\. Customers can resubscribe to your product through AWS Marketplace\. 