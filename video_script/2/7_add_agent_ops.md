## Track the crew with AgentOps

Before we run our crew and have a million dollar song on our hands, let's track the generated output with AgentOps so we have a copy of our song in the cloud for future reference

- Go to https://app.agentops.ai/
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
- Let's download the code provided by AgentOps aka let's download the AgentOps package 
- So we'll now enter the following COMMAND: `poetry add agentops`
- Notice how we still have our import warning showing
- This is because the Poetry framework stores downloaded packages in a location that VSCode doesn't know about by default

## FOR REFERENCE Fixing import warnings

- Here is how we find out where Poetry stores downloaded packages and how we let VSCode know about it
- We enter: `poetry env info`
- And copy the "path" into the interpreter path setting in VSCode
- SHIFT + COMMAND + P
  - `Python: Select Interpreter`
  - Enter interpreter path...

- After we let VSCode know where to look, the import warning goes away
- Notice how we used one tool aka `pip` to install `crewai` onto our machine and we are using another tool aka `poetry` to install packages into our generated CrewAI project

- I know it's confusing but welcome to Python development