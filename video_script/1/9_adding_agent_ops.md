Ok! The way we built this crew of agents manually up from scratch is NOT recommended at all.

BUT for understanding how CrewAI works I hope you found it useful.

As a final quick step for understanding how CrewAI works, let's track our agents using AgentOps...

AgentOps is compatible with many different multi-agent frameworks including CrewAI and will help us track...

A) The cost of each agent in our crew
B) The time each agent takes to complete its tasks and
C) Any errors encountered when executing the tasks given to our crew

and more...

The process of integrating AgentOps is similar to how we integrated with OpenAI

- We go to https://app.agentops.ai/ and create an account
- Provision an API key
- and then add another secret API KEY on a new line in the .env file of our project
- this one will be called AGENTOPS_API_KEY
- `echo "AGENTOPS_API_KEY=" >> .env`
- The final thing to do after that is add the following lines to our `main.py` file
```
import os
import agentops

agentops.init(os.getenv("AGENTOPS_API_KEY"))
```

Be sure to initialize AgentOps BEFORE calling your crew so that tracking is setup before kicking off your tasks

- And now observe how VSCode, our editor, is letting us know the `agentops` import has an issue
- This is because we haven't yet downloaded the `agentsops` package published by the AgentOps team on PyPi
- So..., just like we did for the `crewai` package let's install `agentops`
- `pip install agentops==0.3.12`

After installing `agentops`, we should see the import error go away

## Let's try running the crew our crew again

- `python src/our_crew_of_agents/main.py`

## Check out the AgentOps dashboard

- Observe the additional metrics given to us on the command line
  - Like what the cost to us was of running the crew this session etc.
- And also how the details of this interaction with the agents in our crew was uploaded to AgentOps for reference and review

- As you get deeper into leveraging Agent based workflows you'll need a tool like AgentOps for monitoring how your agents are performing