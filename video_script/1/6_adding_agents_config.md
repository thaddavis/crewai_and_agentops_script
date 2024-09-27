## Let's run our crew again...

- `python src/crew_of_agents/main.py`

## Observe the error

- FileNotFoundError: [Errno 2] No such file or directory: '/code/src/crew_of_agents/config/agents.yaml'

- OK! As we see, the way CrewAI is designed requires us to specify a file called `agents.yaml` that will define how each agent works...

- https://docs.crewai.com/getting-started/Start-a-New-CrewAI-Project-Template-Method/#agentsyaml

- `mkdir -p src/crew_of_agents/config`
- `touch src/crew_of_agents/config/agents.yaml`
```.yaml
george_washington:
  role: >
    American Army General - George Washington
  goal: >
    To lead the American Army to victory in the Revolutionary War.
  backstory: >
    George Washington was born in 1732 in Westmoreland County, Virginia. He was
    the first President of the United States and led the American Army to victory
    in the Revolutionary War. He is known as the "Father of His Country".

thomas_jefferson:
  role: >
    American Founding Father - Thomas Jefferson
  goal: >
    To write the Declaration of Independence and help establish the United States
    as an independent nation.
  backstory: >
    Thomas Jefferson was born in 1743 in Shadwell, Virginia. He was the third
    President of the United States and the principal author of the Declaration of
    Independence. He is known for his role in shaping the early government of the
    United States.
```

AND instead of having a plain ole' default agent in our crew let's configure each agent to use the details outlined in the `agents.yaml` file...

```
@agent
def george_washington(self):
  return Agent(
    config=self.agents_config['george_washington'],
    verbose=True
  )
@agent
def thomas_jefferson(self):
  return Agent(
    config=self.agents_config['thomas_jefferson'],
    verbose=True
  )
```