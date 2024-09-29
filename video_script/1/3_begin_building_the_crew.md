OK! Instead of simply printing a line that says "Telling my agents to do something"...

Let's add in some code provided by the team at CrewAI...

We could use only one `main.py` file for writing all our code BUT that is not advised as it would cause us to constantly be scrolling back and forth as we add more lines

THEREFORE, just so this `main.py` file doesn't get bloated let's create another file...

```
touch src/our_crew_of_agents/crew.py
```

Let's paste in this code that I pieced together by looking at various examples provided by the CrewAI team...

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

and we can call this code in this `crew.py` file from the `main.py` file like this...

```update src/our_crew_of_agents/main.py
from src.our_crew_of_agents.crew import OurCrewOfAgents

print("Calling our crew of agents...")
CrewOfAgents().crew().kickoff()
```

Remember in our Dockerfile how it included a line specifying the PYTHONPATH aka `ENV PYTHONPATH=/code`

This line configures the Python intepreter on our Dev container to look for code we import throughout our project at the specified location.

The complete path to the `crew.py` file is `/code/src/our_crew_of_agents/crew.py`

I know in the Python code that dots are being used instead of slashes to specify the path to the file on the file-system but in this context they mean the same thing...

And also note that when performing imports, you DON'T have to write `.py` at the end the filename

