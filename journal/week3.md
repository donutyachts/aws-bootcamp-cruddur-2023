# Week 3 — Decentralized Authentication

## Watched Ashish's Week 3 - Decenteralized Authentication
Notes:
- [User Pool vs. Identify Pool](https://youtu.be/tEJIeII66pY?t=510)
    - Cognito User Pool = auth using social media sites to offload need to store credentials or direct u/p access to app with storing credentials
    - Cognito Identity Pool = access AWS services using credentials of a third-party
- Lifecycle Management
    - User: employee access to apps within organization from new hire to offboarding (leaving organization)
    - Token: temporary access via token and status (i.e. creation, suspension, etc.) of token

## Watch Chirag Week 3 - Spending Considerations (Not yet posted)
Notes:
- Video not posted in student portal.

## Setup Cognito User Pool
![Proof of Cognito user pool creation 0](/assets/week3-proof-setup-cognito-user-pool.png)
![Proof of Cognito user pool creation 1](/assets/week3-proof-setup-cognito-user-pool-1.png)
![Proof of Cognito user pool creation 2](/assets/week3-proof-setup-cognito-user-pool-2.png)

I enabled the option to send email for the first user manually created, hankcrumb, and received the email from Cognito.
![Proof of Cognito user pool creation 3](/assets/week3-proof-setup-cognito-user-pool-3.jpeg)

Notes:
- Creating the user pool was not diffucult. However, understadning the various options is key. The cruddur app will not store user credentials and does not allow access to AWS services, so a Cognito User Pool was created.

## Implement Custom Signin Page
Tried to sign with a nonexisting user.
![Proof of custom signin page implementation 0](/assets/week3-proof-implement-custom-signin-page.png)

Tried to signin with a user manually created in Cognito.
![Proof of custom signin page implementation 1](/assets/week3-proof-implement-custom-signin-page-1.png)

Tried Chrome and username instead of email to get an error.
![Proof of custom signin page implementation 2](/assets/week3-proof-implement-custom-signin-page-2.png)

Notes:
- Aaargh! Typos. DEFALT rather than DEFAULT. This tripped me up while watching the live stream.
- npm i aws-amplify --save
    - The --save automatically adds aws-amplify as a dependency to package.json

## Implement Custom Signup Page 
Successful signin with a user in Cognito, hankcrumb. Notice the username in the password save prompt is 'hankcrumb' and not an email.
![Proof of custom signup page implementation 1](/assets/week3-proof-implement-custom-signup-page-1.png)

Displays option to 'Sign Out' on lower left.
![Proof of custom signup page implementation 2](/assets/week3-proof-implement-custom-signup-page-2.png)

Successful signin of user in Cognito, hankcrumb. Notice the user's name and handle display on the lower left.
![Proof of custom signup page implementation 3](/assets/week3-proof-implement-custom-signup-page-3.png)

Displays hankcrumb as verified in Cognito.
![Proof of custom signup page implementation 4](/assets/week3-proof-implement-custom-signup-page-4.png)

Notes:
- awscli command to manually create and verfiy a user in an existing Cognito user pool: `aws cognito-idp admin-set-user-password --username hankcrumb --password Testing1234! --user-pool-id ca-central-1_YM6bo6X1E --permanent`

## Implement Custom Confirmation Page
Displays the email from Cognito with verification code. Beforehand, a new user - Nancy Drew, issue129@protonmail.com - was created through the Cruddur signup page.
![Proof of custom confirmation page confirmation 3](/assets/week3-proof-implement-custom-confirmation-page-3.jpeg)

Displays Cruddur confirmation page. This page displays immediately after signup. The confirmation code is in an email sent to the user. See above image.
![Proof of custom confirmation page confirmation 1](/assets/week3-proof-implement-custom-confirmation-page-1.png)

Displays that user that signed up on Cruddur - Nancy Drew - is verified.
![Proof of custom confirmation page confirmation 2](/assets/week3-proof-implement-custom-confirmation-page-2.png)

## Implement Custom Recovery Page
Displays emailf rom Cognito with password reset code. The email is generated after a user uses the 'Forgot Password' page on Cruddur to reset their password.
![Proof of custom recovery page implementation 3](/assets/week3-proof-implement-custom-recovery-page-3.jpeg)

Displays Cruddur 'Recovery your Password' page. The page displays after using the 'Forgot Password' page to send reset the user password.
![Proof of custom recovery page implementation 1](/assets/week3-proof-implement-custom-recovery-page-1.png)

Displays page after successfully resetting the password.
![Proof of custom recovery page implementation 2](/assets/week3-proof-implement-custom-recovery-page-2.png)

## Watch about different approaches to verifying JWTs

Notes:
- I've exhausted my GitPod credits and pondering what route to take: local, GitHub Codespace, or pay for Gitpod.