# Week 1 — App Containerization

### 1. Watch How to Ask for Technical Help (26mm30ss)
Notes: When asking for help, do the heavy lifting and include:
1. Link to article you read about the error.
2. Screenshot of full error.
3. Code snippet.
4. Link to gist with entire code.
5. Link to code committed in repo.
6. Screenshot(s) of troubleshooting done using browser Inspector panel.

### 2. Watched Grading Homework Summaries (06mm42ss)
Notes: Uh-oh, I need to imporve my summaries!

### 3. Watched Week 1 - Live Streamed Video (02hh03mm04ss; same video for item 7)
See item 7.

### 4. Remember to Commit Your Code (01mm55ss)
Notes: I've been using git commands in terminal window of VS to stage `git add <filename>` and commit `git commit -m "Comment."` locally as well as push updates `git push` to the repo. I've also saved updates directly on GitHub. Doing this created a problem when I returned to edit files in VS. The changes I made directly on GitHub where not synced to my local copy of the repo. Going forward, I'll first `git pull` to ensure I get the latest version.

### 5. Watcked Chirag's Week 1 - Spending Considerations (10mm08ss)
Notes: Yes, noticed that the Gitpod environment went inactive after a certain amount of inactivity, 30 minutes.

### 6. Watched Ashish's Week 1 - Container Security Considerations (41mm15ss)
Notes: 
- Secrity everywhere for everything all at once.
- Interesting to know that you can create a private image registry. Security best practice: "Trusting a Private vs Public Image Registry"
- Created Snyk account (vulnerability scanning of Docker files) with GitHub SSO and forked the docker-goof repo. Clone versus fork? Got clarification [here](https://docs.github.com/en/desktop/contributing-and-collaborating-using-github-desktop/adding-and-cloning-repositories/cloning-and-forking-repositories-from-github-desktop). 
> When you clone a repository, any changes you push to GitHub will affect the original repository. To make changes without affecting the original project, you can create a separate copy by forking the repository.
- Remember that Amazon Inspector is for vulnerability scanning of Docker container images.
- I didn't understand how the secrets are rotated using AWS Secrets Manager. Reading more for a live example.
- Ugh. [You have to stop the container to perform a change, security updates, and you cannot run multiple of the same containers at the same time from a single Docker file.](https://www.youtube.com/watch?v=OjZz4D0B-cA&list=PLBfufR7vyJJ7k25byhRXJldB5AiwgNnWv&index=25&t=2272s) AWS has auto-scaling for containers.
-  So much to do and know about security but it's facinating.

![Proof ran Snyk on repo](/assets/week1-proof-scan-vulnerable-repo-with-snyk.png)

Source: [Cloud Security Bootcamp resources](https://www.cloudsecuritybootcamp.com/)

### 7. Containerize Application (Dockerfiles, Docker Compose)
Notes:
- Successfully followed along with the live stream. However, I encountered an issue:
    - After saving text changes in backend-flask/services/home_activities.py they did not reflect on the frontend localhost:3000. Stopped and restarted both containers though now the entire center column of the page (where all the posts would have normally display) is empty though everything else displays on the page.
- Watched live stream recording. Containers made more sense on second pass.
    - During the live stream I had difficulty with port forwarding. I couldn't find the same screens that Andrew showed. Turns out my VSCode is different from his in that I have a [VSCode Exposed Ports tab](/assets/week1-vscode-exposed-ports.png) and [VSCode Ports tab](/assets/week1-vscode-ports.png) tabs.
    - I missed the `unset BACKEND_URL` and `unset FRONTEND_URL` commands on during the live stream. Caught it on second go.
    - Successfully built and ran containers afer some CORS errors unrelated to port numbers. App loads in browser.

![Proof backend and frontend containers running](/assets/week1-proof-containers-running-terminal.png)

![Proof build containers for backend and frontend](/assets/week1-proof-build-containers-backend-frontend.png)

![Proof app runs in browser and data displays](/assets/week1-proof-app-running-in-browser.png)

Source: [Week 1 instructions on omenking's repo shared on live stream](https://github.com/omenking/aws-bootcamp-cruddur-2023/blob/week-1/journal/week1.md)

### 8. Document the Notification Endpoint for the OpenAI Document (32mm13ss; same video for items 9 and 10)
![Proof documentation for notifications endpoint creted in OpenAI document](/assets/week1-proof-documentation-for-notifications-backend-endpoint-created-in-openai-document.png)

### 9. Write a Flask Backend Endpoint for Notifications
Notes:
- Encountered a number of erros in creating the notifications endpoint and all due to improperly tabbing in the python files. I get it since python is tab-sensitive.

![Proof backend notifications endpoint created](/assets/week1-proof-backend-notifications-endpoint-created.png)

### 10. Write a React Page for Notifications
![Proof frontend displays notifications data from backend](/assets/week1-proof-frontend-updated-to-display-notifications-data-from-backend.png)

### 11. Run DynamoDB Local Container and ensure it works (19mm18ss; same video for item 12)

### 12. Run Postgres Container and ensure it works