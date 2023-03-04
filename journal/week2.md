# Week 2 — Distributed Tracing

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
- [Source instructions for getting data from app into Honeycomb](https://docs.honeycomb.io/getting-data-in/opentelemetry/python/)
- Use https://honeycomb-whoami.glitch.me/ to find out from where you got the Honeycomb API key.
- Found a mistake in app.py after watching recording of week 2 live stream. Did not have 'simple' in 'simple_processor'. Added.
- Began using git tags to denote commits corresponding to each week of bootcamp, https://git-scm.com/book/en/v2/Git-Basics-Tagging.