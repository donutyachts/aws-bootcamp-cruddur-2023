# Week 0 — Billing and Architecture

## Homework challenges  
### 1. Destroy your root account, Set MFA, IAM role :white_check_mark:

This challenge confused me because I just don't see how the root account can be deleted, without closing the AWS account, and thereafter set MFA and create a new IAM role on the same AWS account. And AWS documentation simply does not reference directly or indirectly that a root account can be destroyed without closing the AWS account as well, [AWS Account Root User](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html). Sooo, I did the following:

- Enabled MFA on the root account: 
> MFA device assigned
You can register up to 8 MFA devices of any combination of the currently supported MFA types with your AWS account root and IAM user. With multiple MFA devices, you only need one MFA device to sign in to the AWS console or create a session through the AWS CLI with that user.
- Created a new IAM user, administrator.
- Created an admin role group.
- Assigned administrator user to admin role group. (Recommended by AWS.)
- Enabled MFA on the new administrator user.

There are a number of IAM best practices, [Security best practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html). Going forward I will only login to the AWS console using the administrator user unless the root user is required for those few root-user-only tasks.

### 2. Set a billing alarm, Set a AWS Budget :white_check_mark:
This was easy to do. Impressed with ability to not only set alerts but also apply actions to each alert. Did the following:
- Created AWS Budget, MyMonthlyBudget, of $100.
> After creating a budget, it can take up to 24 hours to populate all of your spend data.
- Created billing alert when spend reaches 20, 40, 60, and 80 percent of budget.
- Created billing alert when spend is forecast to reach 100 percent of budget.
- Created billing alert when spend has actually exceeded budget.

Followed this tutorial for creating the AWS Budget and alerts: [Control your AWS costs](https://aws.amazon.com/getting-started/hands-on/control-your-costs-free-tier-budgets/).

### 3. Use EventBridge to hookup Health Dashboard to SNS and send notification when there is a service health issue.
Evidence:

Notes:
- I may return to this, but current I don't have the time to complete.

Source: [Amazon EventBridge setup and prerequisites](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-setup.html)

### 4. Review all the questions of each pillars in the Well Architected Tool (No specialized lens) :white_check_mark:
Evidence:

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

### 5. Create an architectural diagram (to the best of your ability) the CI/CD logical pipeline in Lucid Charts
Evidence:
- [Conceptual and logical diagrams](https://lucid.app/documents/view/988a4404-009f-4940-8455-b961219c18ae)
- [CI/CID diagram](https://lucid.app/documents/view/08729562-4a66-477c-8909-d9f95356db97) (include tools - VS Code, Gitpod, GitHub, AWS, etc. in the diagram)

Notes:
- There is a limit to the number of shapes that Lucidcharts allows across all of your documents, 60 shapes across 3 documents, which I discovered after creating the conceptual and logical diagrams. I created a new free trial account just for the CI/CID pipeline.
- It's not a great diagram, but I will likely return and improve it.
- Understanding the plain language practical application of each step in the pipeline is needed.

Source: [Week 0 - Lucid Charts Lets Recreate the Cruddur Logical Diagram](https://www.youtube.com/watch?v=K6FDrI_tz0k)

### 6. Research the technical and service limits of specific services and how they could impact the technical path for technical flexibility. 
Evidence:

Notes:
- I may return to this, but current I don't have the time to complete.

Sources: 

### 7. Open a support ticket and request a service limit
Evidence:

Notes:
- I may return to this, but current I don't have the time to complete.

Sources:

## Student portal checklist 

### Recreate Conceptual Diagram in Lucid Charts or on a Napkin

- See above.

### Recreate Logical Architectual Diagram in Lucid Charts

- See above.

### Create an Admin User
Proof:
- Created an "administrator" user in the AWS console then configured AWS CLI for the administrator user to show list of users.
![Proof of admin user creation](assets/week0-proof-create-an-admin-user.png)

### Use CloudShell

### Generate AWS Credentials
Proof:
- Generated the access key credentials for "administrator" user.

![Proof that AWS access key credentials generated](assets/week0-proof-generate-aws-credentials.png)

Notes:

Sources:

### Installed AWS CLI
Proof:
- Installed AWS CLI on a Mac. Easy. Used the CLI to display installed version.

![Proof that AWS CLI is installed](assets/week0-proof-installed-aws-cli.png)

Notes: 
- AWS CLI has a command completion feature that you can install. More details on the aws-cli v2 GitHub.

Sources:
- [aws-cli v2 on GitHub](https://github.com/aws/aws-cli/tree/v2)

### Create a Billing Alarm

### Create a Budget



## Cool stuff to attempt when I have time
- Create an Organization, https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html
- Implement an identity provider like Okta for access to the AWS account. (Considered a best practice.)
- Implement secrets management, https://geekflare.com/secret-management-software/

Sources: 
- [External FREE AWS Cloud Project Bootcamp — Outline] (https://docs.google.com/document/d/19XMyd5zCk7S9QT2q1_Cg-wvbnBwOge7EgzgvtVCgcz0/edit#)
- [Updating Your Journal in Github](https://www.youtube.com/watch?v=mWaSBRJhUFM&list=PLBfufR7vyJJ7k25byhRXJldB5AiwgNnWv&index=20)
