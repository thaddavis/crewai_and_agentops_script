## Track the crew with AgentOps

Before we run our crew and have a million dollar song on our hands, let's track the generated output with AgentOps so we have a copy of our song in the cloud for future reference

- Go to https://app.agentops.ai/
- Go to Projects
- + New Project > "Revolutionary War" > `Create Project`
- Copy API key
- add environment variable called AGENTOPS_API_KEY
- `echo "AGENTOPS_API_KEY=" >> .env`
- add the following to `main.py`
```
import os
import agentops

agentops.init(os.getenv("AGENTOPS_API_KEY"))
```
- Observe how VSCode is letting us know the import has an issue
- We want to reuse all the code provided by AgentOps the company for tracking metrics related to our crew
- Let's download the code provided by AgentOps aka let's download the AgentOps package 

- There are various tools in the Python ecosystem for downloading 3rd party code
- pip is the default tool that comes with Python but over the past few years another tool called `Poetry` has risen in popularity and this is CrewAI recommends us to use
- Poetry does a number of things (that we won't get into) but one of the things that it can do is download 3rd party python code
- So we'll now enter the following COMMAND: `poetry add agentops`