The way we built this crew of agents manually up from scratch is NOT recommended at all.

BUT for understanding how CrewAI works I hope you found it useful.

Before we wrap up, let's do one final thing which is show how to track our agents using AgentOps...

AgentOps is compatible with many different multi-agent frameworks, including CrewAI, and will help us track things like...

A) The cost of each agent in our crew
B) The time each agent takes to complete its tasks
and C) Any errors encountered when executing tasks

The process of integrating AgentOps is very easy and is similar to how we integrated OpenAI...

- Create an account on AgentsOps platofrm (https://app.agentops.ai/)
- Provision and copy an API key
- and then add another entry to the .env file on a new line like so...
- `echo "AGENTOPS_API_KEY=" >> .env`
- After adding this API key to our project when then have to add 3 lines to our code...
```
import os
import agentops

agentops.init(os.getenv("AGENTOPS_API_KEY"))
```

These lines allow agentops to track the activity of any compatible agents in our project...

Be sure to initialize AgentOps BEFORE calling the crew so that tracking is set up before running tasks

- AND holdup! Observe how VSCode, our editor, is indicating that the `agentops` import has an issue
- This is because we haven't yet downloaded the `agentsops` package published by the AgentOps team from PyPi
- So just like we did for the `crewai` package let's install `agentops`
- `pip install agentops==0.3.12`

After installing `agentops`, we should see the import error go away

## Let's now run the crew again and see what happens

- `python src/our_crew_of_agents/main.py`

## Check out the AgentOps dashboard

- Observe the additional metrics given to us on the command line
  - Like what the cost was of running the crew this session etc.

- And also note how the details of this interaction with our crew was uploaded to AgentOps for reference and review

- As you get deeper into leveraging Agent based workflows you'll need a tool like AgentOps for monitoring how your agents are performing