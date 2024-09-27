- `python src/crew_of_agents/main.py`
- Observe the additional metrics given to us on the command line
  - Like what the cost to us was of running the crew this session etc.
- And also how the details of this interaction with the agents in our crew was uploaded to AgentOps for reference and review

- As you get deeper into leveraging Agentic workflows you'll need a tool like AgentOps for monitoring how your agents are performing from a variety of angles

The last I'll do is record the exact versions of `crewai` and `agentops` we used in this project so if we ever revisit this in the future we know exactly what was used...

One of the conventional filenames we use for doing this is called requirements.txt...

`touch requirements.txt`
```
agentops==0.3.12
crewai==0.63.6
```