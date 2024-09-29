OK! Instead of simply printing a line that says "Telling my agents to do something"...

Let's add in some code provided by the team at CrewAI and call it from our `main.py` script...

When building an application we could include all our code in one big ole' file BUT that is not advised as it would cause us long term to constantly be scrolling back and forth when reading or making edits...

THEREFORE, just so our main file doesn't get bloated with too many lines let's create another file...

```
touch src/our_crew_of_agents/crew.py
```

Let's paste in this code that I pieced together by looking at various examples provided by the CrewAI team in their examples repo...

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

And we can call the code in this 2nd file (called `crew.py`) from `main.py` like this...

```update src/our_crew_of_agents/main.py
from src.our_crew_of_agents.crew import OurCrewOfAgents

print("Calling our crew of agents...")
CrewOfAgents().crew().kickoff()
```

Remember in our Dockerfile how it included a line specifying the PYTHONPATH aka `ENV PYTHONPATH=/code`

This line configures the Python intepreter on our "mini-machine" to look for code we import throughout our project at the specified location.

The complete path to the `crew.py` file is `/code/src/our_crew_of_agents/crew.py`

I know in the Python code dots are being used instead of slashes but in this context they mean the same thing

They tell the computer where to look for the code we want to use

And also note that when performing imports throughout your project, you DON'T have to write `.py` at the end the filename