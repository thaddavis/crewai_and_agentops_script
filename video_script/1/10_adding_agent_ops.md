Ok! The way we built this crew of agents up from scratch is NOT recommended. But for understanding how CrewAI works it definitely was fun.

Next, we will build another crew using the approach recommended by CrewAI...

https://docs.crewai.com/getting-started/Start-a-New-CrewAI-Project-Template-Method/#creating-a-new-project

BUT! Before we do that...

Let's now track this simple crew using AgentsOps to get in the habit of tracking our agents...

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
- `pip install agentops`