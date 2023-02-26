# Week 0 — Billing and Architecture

[Go to index](/journal/index.md)

### 1. Watched Week 0 - Live Streamed Video
Notes: Attended live stream.

### 2. Watched Chirag's Week 0 - Spend Considerations
Notes:
- To my surprise I had to enable access to billing data for non-root users because the new user I created, administrator, with administrator roles does not automatically have read/write access to billing data. 
- Also surprised to learn that AWS supports the creation of policies to read/write billing data on a _per page_ basis! In other words, you crate a policies that allows a user to read/write only to certain billing data screens/section in the AWS account. Granular indeed but also cool. 
- The Cost Allocations Tags were interesting since this is probably needed when a company's Finance team needs to reconcile AWS costs to the corresponding team using the AWS account.

Source: [AWS IAM tutorial: Delegate access to billing console](https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_billing.html?icmpid=docs_iam_console#tutorial-billing-step2)

### 3. Watched Ashish's Week 0 - Security Considerations
Notes:
- Liked Ashish's overview of the types of Organization Unit hierarchy that could be used such as Active Accounts and Standby Accounts or based on business unit such as Engineering BU or Finance BU.
- I have two separate AWS accounts that I created a different times: one non-free tier and one free tier. Although not covered in the video, I had to take send an invitation in order to get the existing account to display underneath an OU. Pretty cool.
- Cloned [Ashish's SCP repo](https://github.com/hashishrajan/aws-scp-best-practice-policies) and created/applied the Prevent Leave Organization SCP.

![Proof of attempt to list SCP](/assets/week0-proof-security-aws-organizations-servcie-control-policy.png)

The administrator user created doesn't have permissions to Organizations. Tried this after creating Organzation and adding free tier account into the Organization of a non-free tier account. 

Source: [Exmample service control policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_examples.html)

### 4. Recreate Conceptual Diagram in Lucid Charts or on a Napkin
- [Conceptual and logical diagrams](https://lucid.app/documents/view/988a4404-009f-4940-8455-b961219c18ae)
- [CI/CID diagram](https://lucid.app/documents/view/08729562-4a66-477c-8909-d9f95356db97) (include tools - VS Code, Gitpod, GitHub, AWS, etc. in the diagram)

Notes:
- There is a limit to the number of shapes that Lucidcharts allows across all of your documents, 60 shapes across 3 documents, which I discovered after creating the conceptual and logical diagrams. I created a new free trial account just for the CI/CID pipeline.
- It's not a great diagram, but I will likely return and improve it.
- Understanding the plain language practical application of each step in the pipeline is needed.

Source: [Week 0 - Lucid Charts Lets Recreate the Cruddur Logical Diagram](https://www.youtube.com/watch?v=K6FDrI_tz0k)

### 5. Recreate Logical Architectual Diagram in Lucid Charts
See above.

### 6. Create an Admin User (Destroy your root account, Set MFA, IAM role)
![Proof of admin user creation](/assets//week0-proof-create-an-admin-user.png)

Notes:
- Created an "administrator" user in the AWS console then configured AWS CLI for the administrator user to show list of users.

This challenge confused me because I just don't see how the root account can be deleted, without closing the AWS account, and thereafter set MFA and create a new IAM role on the same AWS account. And AWS documentation simply does not reference directly or indirectly that a root account can be destroyed without closing the AWS account as well, [AWS Account Root User](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html). Sooo, I did the following:

- Enabled MFA on the root account: 
> MFA device assigned
You can register up to 8 MFA devices of any combination of the currently supported MFA types with your AWS account root and IAM user. With multiple MFA devices, you only need one MFA device to sign in to the AWS console or create a session through the AWS CLI with that user.
- Created a new IAM user, administrator.
- Created an admin role group.
- Assigned administrator user to admin role group. (Recommended by AWS.)
- Enabled MFA on the new administrator user.

There are a number of IAM best practices, [Security best practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html). Going forward I will only login to the AWS console using the administrator user unless the root user is required for those few root-user-only tasks.

### 7. Use CloudShell
![Proof that I used CloudShell](/assets/week0-proof-use-cloudshell.png)

### 8. Generate AWS Credentials
![Proof that AWS access key credentials generated](/assets//week0-proof-generate-aws-credentials.png)

Notes: Generated the access key credentials for "administrator" user.

### 9. Installed AWS CLI
![Proof that AWS CLI is installed](/assets/week0-proof-installed-aws-cli.png)

Notes:
- Installed AWS CLI on a Mac. Easy. Used the CLI to display installed version.
- AWS CLI has a command completion feature that you can install. More details on the aws-cli v2 GitHub.
- I don't know why it doesn't display in .gitpod.yml though I installed the CLI after using GitPod.

Sources:
- [aws-cli v2 on GitHub](https://github.com/aws/aws-cli/tree/v2)
- [AWS CLI Command Reference](https://awscli.amazonaws.com/v2/documentation/api/latest/index.html)

### 10. Create a Billing Alarm
![Proof of billing alarms created](/assets/week0-proof-create-a-billing-alarm.png)

- This was easy to do. Impressed with ability to not only set alerts but also apply actions to each alert. Did the following:
- Created AWS Budget, MyMonthlyBudget, of $100.
> After creating a budget, it can take up to 24 hours to populate all of your spend data.
- Created billing alert when spend reaches 20, 40, 60, and 80 percent of budget.
- Created billing alert when spend is forecast to reach 100 percent of budget.
- Created billing alert when spend has actually exceeded budget.

Followed this tutorial for creating the AWS Budget and alerts: [Control your AWS costs](https://aws.amazon.com/getting-started/hands-on/control-your-costs-free-tier-budgets/).

### 11. Create a Budget
See above.

## Other
### Use EventBridge to hookup Health Dashboard to SNS and send notification when there is a service health issue.
Notes: I may return to this, but current I don't have the time to complete.

Source: [Amazon EventBridge setup and prerequisites](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-setup.html)

### Review all the questions of each pillars in the Well Architected Tool (No specialized lens)
![Week 0 Well-Architected Tool](https://user-images.githubusercontent.com/95940735/219872974-08a1a6e2-0428-4712-9127-46341af6c812.png)

Notes:
- Andrew's suggestion, in his video, was to write what you did for each of the 58 questions. However, I thought this excessive mainly because what I did  would be thoroughly fabricated. 
- It was interesting that the six pillars are not solely tech-centred but also about the organization, team members, and cost.
- Favourite questions:
  - Operational Excellence: OPS 6. How do you mitigate deployment risks?
  - Security: SEC 10. How do you anticipate, respond to, and recover from incidents? Run game days
  - Reliability: REL 4. How do you design interactions in a distributed system to prevent failures? Make all responses idempotent
  - Cost Optimization: COST 2. How do you govern usage?, COST 3. How do you monitor usage and cost? COST 4. How do you decommission resources?
  - Sustainability: SUS 4. How do you take advantage of data access and usage patterns to support your sustainability goals?

Sources:
- [AWS lens](https://docs.aws.amazon.com/wellarchitected/latest/userguide/aws-lenses.html)
- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)
- [Week 0 - Homework Idea (Well Architected Tool)](https://www.youtube.com/watch?v=i-hOfAJb3cE)

### Cool stuff to attempt when I have time
- Implement an identity provider like Okta for access to the AWS account. (Considered a best practice.)
- Implement secrets management, https://geekflare.com/secret-management-software/