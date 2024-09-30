## Observe the error

- FileNotFoundError: [Errno 2] No such file or directory: '/code/src/our_crew_of_agents/config/agents.yaml'

- The way CrewAI is designed requires us to include an `agents.yaml` file at this specific location

- https://docs.crewai.com/getting-started/Start-a-New-CrewAI-Project-Template-Method/#agentsyaml

SO let's add this file like so...

- `mkdir -p src/our_crew_of_agents/config`
- `touch src/our_crew_of_agents/config/agents.yaml`

and paste in the following content...

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

Around the time of recording, in October 2024, the content of this `agents.yaml` file has to follow the structure shown here ...

- https://docs.crewai.com/core-concepts/Agents/

```
name_of_agent:
  role: <TEXT_DESCRIBING_THE_ROLE_OF_THE_AGENT_IN_THE_CREW>
  goal: <TEXT_DESCRIBING_THE_GOAL_OF_THE_AGENT>
  backstory: <TEXT_DESCRIBING_THE_BACKSTORY_OF_THE_AGENT>
```

There are other properties beside the role, goal, and backstory we can give to our agents, but these are the required ones by CrewAI's framework the others properties are optional

(PAUSE)

FYI: This way of outlining configuration is extremely common in programming and is called YAML format...

YAML allows you to specify key-value pairs of information that can be nested at various levels...

In the context of a .yaml file, the `>` (angled bracket) character is called a "folded block" symbol. This character allows you to write the value associated with a key or property on multiple lines instead of one big, long line 

(PAUSE)

The way we connect this `agents.yaml` config to our crew in the `crew.py` file is like this...

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

(PAUSE)

So, zooming out, we can see our Crew class is coming together nicely...

For the beginners, a class in the context of programming is a blueprint for creating things.

To use another cooking analogy...

Imagine a recipe for making an amazing dish. The recipe tells us the ingredients and steps needed to make the dish, but it’s not the actual dish - it's just the instructions for how to make it.

Similarly, a "class" defines the ingredients (or components) of code. When we pass a class to the interpreter of a particular programming language, for example the Python interpreter, we get runnable code that is based on the blueprint outlined in the class

So, with this class, we can see we're designing a crew of agents with one of the agents being gw & the other being tj

(PAUSE)

## Let's try running our crew again

- Now that we've defined the details of the agents in our crew, let's try running them again...

- `python src/our_crew_of_agents/main.py`

- Ok we see a different error which is great. That means we fixed the issue related to the missing `agents.yaml` file

## Observe the error

- FileNotFoundError: [Errno 2] No such file or directory: '/code/src/our_crew_of_agents/config/tasks.yaml'

I wonder what this means...

Dun, Dun, Dun...