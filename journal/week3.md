# Week 3 — Decentralized Authentication

## Watched Ashish's Week 3 - Decenteralized Authentication

## Watch Chirag Week 3 - Spending Considerations (Not yet posted)

## Setup Cognito User Pool
![Proof of Cognito user pool creation](/assets/week3-proof-setup-cognito-user-pool.png)

![Proof of Cognito user pool creation 1](/assets/week3-proof-setup-cognito-user-pool-1.png)

![Proof of Cognito user pool creation 2](/assets/week3-proof-setup-cognito-user-pool-2.png)

![Proof of Cognito user pool creation 3](/assets/week3-proof-setup-cognito-user-pool-3.jpeg)

## Implement Custom Signin Page
![Proof of custom signin page implementation](/assets/week3-proof-implement-custom-signin-page.png)

![Proof of custom signin page implementation 1](/assets/week3-proof-implement-custom-signin-page-1.png)

![Proof of custom signin page implementation 2](/assets/week3-proof-implement-custom-signin-page-2.png)

Notes:
- Aaargh! Typos. DEFALT rather than DEFAULT.
- npm i aws-amplify --save
    - The --save automatically adds aws-amplify as a dependency to package.json
- The error message differs from browser to browser. For example, the above screenshots displays the error message in FF and Chrome.

## Implement Custom Signup Page 
![Proof of custom signup page implementation 1](/assets/week3-proof-implement-custom-signup-page-1.png)

![Proof of custom signup page implementation 2](/assets/week3-proof-implement-custom-signup-page-2.png)

![Proof of custom signup page implementation 3](/assets/week3-proof-implement-custom-signup-page-3.png)

![Proof of custom signup page implementation 4](/assets/week3-proof-implement-custom-signup-page-4.png)

Notes:
- awscli command to manually create and verfiy a user in an existing Cognito user pool: `aws cognito-idp admin-set-user-password --username hankcrumb --password Testing1234! --user-pool-id ca-central-1_YM6bo6X1E --permanent`

## Implement Custom Confirmation Page
![Proof of custom confirmation page confirmation 1](/assets/week3-proof-implement-custom-confirmation-page-1.png)

![Proof of custom confirmation page confirmation 2](/assets/week3-proof-implement-custom-confirmation-page-2.png)

![Proof of custom confirmation page confirmation 3](/assets/week3-proof-implement-custom-confirmation-page-3.jpeg)

## Implement Custom Recovery Page
![Proof of custom recovery page implementation 1](/assets/week3-proof-implement-custom-recovery-page-1.png)

![Proof of custom recovery page implementation 2](/assets/week3-proof-implement-custom-recovery-page-2.png)

![Proof of custom confirmation page confirmation 3](/assets/week3-proof-implement-custom-confirmation-page-3.jpeg)

## Watch about different approaches to verifying JWTs