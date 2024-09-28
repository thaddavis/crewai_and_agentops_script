## Track the crew with AgentOps

Here is how we add AgentOps

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
- So let's download the AgentOps package from PyPi
- Because this project is Python Poetry based, we'll enter the following COMMAND: `poetry add agentops`
- Notice though how we still have our import warning showing
- This is because the Poetry framework stores downloaded packages in a location that VSCode doesn't know about by default

## FOR REFERENCE Fixing import warnings

- Here is how we find out where Poetry stores any downloaded packages and how we let VSCode know about it
- We enter: `poetry env info`
- And copy the "path" into the interpreter path setting of VSCode
- SHIFT + COMMAND + P
  - `Python: Select Interpreter`
  - Enter interpreter path...

- After we let VSCode know where to look, the import warning goes away
- Notice how we used one tool aka `pip` to install `crewai` onto our machine globally for using the CrewAI CLI and we are using another tool aka `poetry` to install packages into our generated CrewAI project

- I know it's confusing but welcome to Python development