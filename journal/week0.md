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
### 4. Review all the questions of each pillars in the Well Architected Tool (No specialized lens)
### 5. Create an architectural diagram (to the best of your ability) the CI/CD logical pipeline in Lucid Charts
### 6. Research the technical and service limits of specific services and how they could impact the technical path for technical flexibility. 
### 7. Open a support ticket and request a service limit

## Learnings from week 0
Problem: There is soooo much documentation from AWS and generally online from tons of people about the same topics that it becomes overwhelming. It's like the cereal aisle at Freshco. So. Many. Choices.

Decision: I've decided to begin with AWS documentation and search elsewhere only if I need for more context or examples. These are my reasons:
- The AWS documentation is actually good. Plus, I'll increase my familiarity with AWS documentation particularly where to find the good stuff and begin bookmarking the heck out of it. AWS must have a hundred plus team just on documention. Sheesh. Take me to the source.
- The value add of non-authoritative or non-AWS documentation is a bit iffy. Searching online and scanning multiple websites wastes time especially when these articles are duplicates of each other. The authors likely read the AWS documentation or someone else's article and then wrote their article for personal clout. The exception, of course, are articles from authoritative sources or any source that adds value (i.e. gives insight or imparts knowledge beyond click-throughs).

## Cool stuff to attempt
- Create an Organization, https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html
- Implement an identity provider like Okta for access to the AWS account. (Considered a best practice.)
- Implement secrets management, https://geekflare.com/secret-management-software/
