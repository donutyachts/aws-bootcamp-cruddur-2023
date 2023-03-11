# Week 2 — Distributed Tracing

## Watch Week 2 Live-Stream Video
Notes:
- Attended live stream.
- Watched the recording.

## Watch Chirag Week 2 - Spending Considerations
Notes:
- Rollbar free tier includes 5k events per month and data retention up to 30 days.
- AWS X-Ray includes 100k traces recorded per month. It is an always free service.
- AWS CloudWatch free tier includes 5GB of log data ingestion and 5 GB log data archive. It is an always free service.

## Watched Ashish's Week 2 - Observability Security Considerations
Notes:
- Observability vs. Monitoring
    - observability looks at the lifecycle of the application holistically; behaviour
    - monitoring checks uptime of application and if error occurs; event

## Instrument Honeycomb with OTEL
![Proof 1 of Honeycomb instrumentation with OTEL](/assets/week2-proof-instrument-honeycomb-with-otel-1.png)

![Proof 2 of Honeycomb instrumentation with OTEL](/assets/week2-proof-instrument-honeycomb-with-otel-2.png)

Notes:
- Environment variables
    - If you do not export the env var, then env var is available only in current shell. 
    - However, if you do export the env var, then subshells will also get the env var. 
    - After setting env var, commit changes, push, and restart Gitpod so that parallel shells recognize the env var.
    - Check that env var are set in Gitpod (gp export) by going here: https://gitpod.io/user/variables 
- Best practice: Use a single API key per project and use the same service name for different components of same project.
- OTEL = Open Telemetry, https://opentelemetry.io/. See also [Cloud Native Computing Foundation](https://www.cncf.io/).
- Added 'init: npm install' to .gitpod.yml, https://docs.npmjs.com/cli/v6/commands/npm-install/.
- [Source instructions](https://docs.honeycomb.io/getting-data-in/opentelemetry/python/) for getting data from app into Honeycomb.
- Use https://honeycomb-whoami.glitch.me/ to find out from where you got the Honeycomb API key.
- Found a mistake in app.py after watching recording of week 2 live stream. Did not have 'simple' in 'simple_processor'. Added.
- Began using git tags to denote commits corresponding to each week of bootcamp, https://git-scm.com/book/en/v2/Git-Basics-Tagging.

## Instrument AWS X-Ray
![Proof 1 of AWS X-Ray instrumentation](/assets/week2-proof-instrument-aws-xray-1.png)

![Proof 1 of AWS X-Ray instrumentation](/assets/week2-proof-instrument-aws-xray-2.png)

Notes:
- Info for install: [AWS X-Ray SDK for Python](https://github.com/aws/aws-xray-sdk-python)
- Find the Groups and Rules by going to Cloudwatch > Settings > Traces > View settings.
- A note about what the daemon options mean: https://docs.aws.amazon.com/xray/latest/devguide/xray-daemon-configuration.html
- Nightmare of a time getting data to X-Ray. Logs shows 'Starting proxy http server on 0.0.0.0:2000' but no data is sent. Appears to stall or hang. This is the [exact issue described by other bootcampers](https://discord.com/channels/1055552619441049660/1079890204019654666). Tried both of the suggestions - docker compose restart and destroy and rebuild everything - though the issue persists. At wit's end.
    - Watched the live stream recording and it seems I initially missed the step of adding the X-Ray daemon in the docker-compose.yml file. ): Must have been that snack I got up to get during the live stream.

## Instrument AWS X-Ray Subsegments
![New error after X-Ray implementation 1](/assets/week2-error-after-xray-implementation-1.png)

![New error after X-Ray implementation 2](/assets/week2-error-after-xray-implementation-2.png)

![New error after X-Ray implementation 3](/assets/week2-error-after-xray-implementation-3.png)

![New error after X-Ray implementation 4](/assets/week2-error-after-xray-implementation-4.png)

Notes:
- Watched the video but neither the error displayed in the video nor in Olga's article applied to me. 
    - Interestingly enough I was not getting any errors after the X-Ray video. 
    - After the X-Ray instrumentation I began to get the above error. 
        > No routes matched location "/@andrewbrown" 
    - After spending time comparing code from Andrew's week-2-xray-subsegments branch and mine and some other useless attempts, I just let it be to preserve my sanity.

## Configure custom logger to send to CloudWatch Logs
![Proof of logs going to CloudWatch 1](/assets/week2-proof-configure-custom-logger-to-send-to-cloudwatch-logs-1.png)

![Proof of logs going to CloudWatch 2](/assets/week2-proof-configure-custom-logger-to-send-to-cloudwatch-logs-2.png)

Notes:
- Left CloudWatch and X-Ray enabled.

## Integrate Rollbar and capture and error
![No routes matched location "/rollbar/test" error](/assets/week2-error-no-routes-matched-location.png)

Notes:
- Watched the video, but plagued by the same error as above. Posted [message on Discord week-2-tracing](https://discord.com/channels/1055552619441049660/1082342191516635146) channel.
    > No routes matched location "/@andrewbrown" 

## Learnings
- Commit code immeditely after making the relevant change. Do not allow edits to multiple files and for various purposes accumulate. Reasons:
    - If you make one big commit across multiple files, then the comment in your commit applies to all files. 
    - Multiple, smaller, and more frequent commits means your comment is specific to the commit. And very useful if you ever need to revert changes.
- Always 'docker compose up' after adding modules to requirements.txt otherwise you can expect to see a module not found error.
