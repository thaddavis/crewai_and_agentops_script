OK! Now instead of simply printing a line that says "Tell my crew of agents to do something", let's do something more interesting...

Let's import some of the official code provided by CrewAI and call it from our `main.py` script...

When building an application we could include all our code in one file BUT that not advised as that would cause us long term to constantly be scrolling back and forth when reading it or making edits...

THEREFORE, just so our main file doesn't get bloated with too many lines let's create another file...

```
touch src/our_crew_of_agents/crew.py
```

Now let's past in the following code that I pieced together by looking at various examples provided by CrewAI in their public examples repository...

https://github.com/crewAIInc/crewAI-examples/blob/main/marketing_strategy/src/marketing_posts/crew.py

```add to src/our_crew_of_agents/crew.py
from crewai import Crew, Process
from crewai.project import CrewBase, agent, crew

@CrewBase
class OurCrewOfAgents():
	@agent
	def george_washington(self):
		return Agent()
	@agent
	def thomas_jefferson(self):
		return Agent()
	@crew
	def crew(self) -> Crew:
		return Crew(
			agents=self.agents,
			tasks=[],
			process=Process.sequential,
			verbose=True,
		)
```

And we can call the code in this other file called `crew.py` like this...

```update src/our_crew_of_agents/main.py
from src.our_crew_of_agents.crew import OurCrewOfAgents

print("Calling our crew of agents...")
CrewOfAgents().crew().kickoff()
```

Remember in our Dockerfile how it included the line specifying the PYTHONPATH aka `ENV PYTHONPATH=/code`

This file configures the Python intepreter on our "mini-machine" to look for imported code at that location.

The complete path to the crew.py file is `/code/src/our_crew_of_agents/crew.py`

When importing python code into various places throughout your project you DON'T have to specify the `.py` at the end of the imported file