# lambda-ec2
Lambda function identifies stale EBS snapshots that are not associated with an active EC2 instance and deletes them to save on storage costs.

![pic](https://github.com/user-attachments/assets/e6bbac64-e55e-4036-879f-6047ed4d3ae2)

**Problem Statement:** Developers in an organization forgot to delete EBS volume snapshots after working on EC2 instances. When snapshots go unnoticed for a while, they lead to unnecessary cloud costs, which can be simply avoided by notifications or by automating the removal of such stale resources.

**To solve this**, I opted to delete them by leveraging AWS Lambda function that runs a custom Python script that:

- Retrieves all EBS snapshots in the user account.
- Filters out stale snapshots that haven’t been accessed in a while.
- Deletes those identified stale snapshots.

To follow the principle of least privilege, I was picky with the custom IAM policies and to fully automate the flow, a cron job was set up using AWS CloudWatch and EventBridge to trigger the Lambda function at selected intervals that ensure timely cleanup.

https://lnkd.in/gxTetiqF

Credits: Abhishek Veeramalla

hashtag#Lambda hashtag#CostOptimization hashtag#AWS hashtag#DevOps
