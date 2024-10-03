## Track the crew with AgentOps

Here's how easy it is to add AgentOps...

- Create an account on app.agentops.ai
- Find the API keys section...
- Copy the default API key
- and then add this API key to the .env like so...
- `echo "AGENTOPS_API_KEY=" >> .env`
- afterwards add the following lines to the `main.py` file of the CrewAI project
```
import os
import agentops

agentops.init(os.getenv("AGENTOPS_API_KEY"))
```
- But observe how VSCode is letting us know the `agentops` import has an issue
- This is because the Python interpreter can't find the `agentops` package on our machine 
- So let's download the AgentOps package from PyPi. Because this project is Poetry based however, we have to use the following COMMAND: `poetry add agentops==0.3.12`
- IF this was a standard Python project we would normally type: `pip install agentops` BUT because it's a Poetry-based project we have to use the `poetry add <PACKAGE_NAME>` command
- Furthermore, note how even though we added our `agentops` package correctly, we still have a warning showing in VSCode
- This is because the Poetry framework stores downloaded packages in a location that VSCode doesn't know about by default

- Here's how we fix this minor issue...

- First, we find out where Poetry stores it's downloaded packages: `poetry env info`
- And then we copy this "path" value into the interpreter path setting of VSCode like so...
- SHIFT + COMMAND + P
  - `Python: Select Interpreter`
  - Enter interpreter path...

- After we let VSCode know where to look, the import warning goes away
- In summary, we used one tool aka `pip` to install `crewai` onto our Dev Container for accessing the CrewAI CLI and how we are using another tool aka `poetry` for installing packages into our generated CrewAI project

- I know it's confusing but welcome to Python development