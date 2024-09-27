## Let's run our crew again...

- `python src/our_crew_of_agents/main.py`

## Observe the error

- FileNotFoundError: [Errno 2] No such file or directory: '/code/src/our_crew_of_agents/config/agents.yaml'

- The way CrewAI is designed requires us to specify a file called `agents.yaml` that will define how each agent in our group of agents works...

- https://docs.crewai.com/getting-started/Start-a-New-CrewAI-Project-Template-Method/#agentsyaml

This `agents.yaml` file has to be placed in a specific location to work...

- `mkdir -p src/our_crew_of_agents/config`
- `touch src/our_crew_of_agents/config/agents.yaml`

And it this `agents.yaml` file we place the configuration for the agents in our crew

As of 9-27-2024 and crewai v0.64.0, the configuration of each agent in this file follows the specific structure shown here...

```
name_of_agent:
  role: <TEXT_DESCRIBING_THE_ROLE_OF_THE_AGENT_IN_THE_CREW>
  goal: <TEXT_DESCRIBING_THE_GOAL_OF_THE_AGENT>
  backstory: <TEXT_DESCRIBING_THE_BACKSTORY_OF_THE_AGENT>
```

For example, let's paste in this config for the agents in our crew...

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

In the context of a .yaml file, the `>` is called a "folded block" symbol and it allows you to write your text on multiple lines instead of one big, long line 

The way we connect this `agents.yaml` configuration to our crew is like so...

Inside our crew.py we have what is a called a "class"

A class is in the context of programming is a blueprint for creating things.

To use another cooking analogy...

Imagine a recipe for making an amazing dish. The recipe tells us the ingredients and steps needed to make the dish, but it’s not the actual dish - it's just the instructions.

Similarly, a "class" defines the ingredients and components of code. When we pass a class to the interpreter of a particular programming language, for example the Python interpreter, we get runnable code that is based on the blueprint outlined in the class that we can then use and interact with.

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

Here we see that we're designing our crew to consist of 2 agents (gw & tj) and just so we don't bloat this file with too many lines, we use the configuration found in the config folder to specify how each agent works

## Let's try running our crew again

- `python src/our_crew_of_agents/main.py`

- Ok we see something new being spit out which is great. That means we fixed the issue related to the missing `agents.yaml` file

## Observe the error

- FileNotFoundError: [Errno 2] No such file or directory: '/code/src/our_crew_of_agents/config/tasks.yaml'

Dun, Dun, Dun...