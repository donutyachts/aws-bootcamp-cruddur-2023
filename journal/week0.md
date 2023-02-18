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
[Amazon EventBridge setup and prerequisites](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-setup.html)

### 4. Review all the questions of each pillars in the Well Architected Tool (No specialized lens)
[AWS lens](https://docs.aws.amazon.com/wellarchitected/latest/userguide/aws-lenses.html) aka additional best practices that are not part of the [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/). And here's the video Andrew made for this question: [Week 0 - Homework Idea (Well Architected Tool)](https://www.youtube.com/watch?v=i-hOfAJb3cE)

Some of my favourite questions:
- Operational Excellence: OPS 6. How do you mitigate deployment risks?
- Security: SEC 10. How do you anticipate, respond to, and recover from incidents? Run game days
- Reliability: REL 4. How do you design interactions in a distributed system to prevent failures? Make all responses idempotent
- Cost Optimization: COST 2. How do you govern usage?, COST 3. How do you monitor usage and cost? COST 4. How do you decommission resources?
- Sustainability: SUS 4. How do you take advantage of data access and usage patterns to support your sustainability goals?

![Week 0 Well-Architected Tool](https://user-images.githubusercontent.com/95940735/219872974-08a1a6e2-0428-4712-9127-46341af6c812.png)

Thoughts:
- Andrew's suggestion, in his video, was to write what you did for each of the 58 questions. However, I thought this excessive mainly because what I did  would be thoroughly fabricated.
- Interesting that these six pillars are not solely tech-centred but also about the organization, team members, and cost.

### 5. Create an architectural diagram (to the best of your ability) the CI/CD logical pipeline in Lucid Charts
This morning's (Sat-11-Feb-2023) week 0 live stream walked through the creation of the conceptual diagram for Crudder. I followed along and cleaned up the diagram. Go here for the [Crudder diagrams (conceptual, logical) on Lucidchart](https://lucid.app/documents/view/988a4404-009f-4940-8455-b961219c18ae)
### 6. Research the technical and service limits of specific services and how they could impact the technical path for technical flexibility. 
### 7. Open a support ticket and request a service limit

## High level thoughts from week 0

| No. | Thoughts | Conclusions |
|-----:|---------------|---------------|
|     1|There is soooo much documentation from AWS and generally online from tons of people about the same topics that it becomes overwhelming. It's like the cereal aisle at Freshco. So. Many. Choices.|I've decided to begin with AWS documentation and search elsewhere only if I need more context or examples. These are my reasons: (A) The AWS documentation is actually good. Plus, I'll increase my familiarity with AWS documentation particularly where to find the good stuff and begin bookmarking the heck out of it. AWS must have a hundred plus team just on documention. Sheesh. Take me to the source. (B) The value add of non-authoritative or non-AWS documentation is a bit iffy. Searching online and scanning multiple websites wastes time especially when these articles are duplicates of each other. The authors likely read the AWS documentation or someone else's article and then wrote their article. The exception, of course, are articles from authoritative sources or any source that adds value (i.e. gives insight or imparts knowledge beyond click-throughs).|
|     2|How much time I am spending on the homework challenges and the bootcamp in general?|I'll need to start tracking my time. Not to the level of detail where I could invoice for my time, but enough so that I have some metrics per week and for the entire bootcamp. Potential employers would be interested to know.|
|     3|During the week 0 live stream Margaret provided a good scenario of how various stakeholders talk about their needs and generally how collecting requirements occurs. There was an emphasis on the following: (A) stakeholder requirements are incomplete, ill-defined, and unrealistic, (B) requirements collection is done in a fast, haphazard, and disorganized manner, (C) requirements are conveyed from stakeholder directly to tech team. This scenario seems to imply a friction between business and tech teams. Chris later mentions RRAC (requirements, risks, assumptions, constraints) as a things to check-off when collecting requirements as well as asking the "dumb" but revealing questions. Shala later still mentioned how she is new to DevOps and that employers were very interested in her ability to explain concepts to non-technical stakeholders more so than her tech skills. There are Business Analysts and Project Managers who also do requirements management though they went unmentioned. It appears that, in broad strokes, tech teams are being forced to extend their skillset beyond tech. And companies then enjoy a flat organizational hierarchy.|I could be misunderstanding the real world day-to-day of a DevOps Engineer, but it would be interesting to review other DevOps-focused training material to see how they talk about requirements gathering and management.       |

## Cool stuff to attempt
- Create an Organization, https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html
- Implement an identity provider like Okta for access to the AWS account. (Considered a best practice.)
- Implement secrets management, https://geekflare.com/secret-management-software/
