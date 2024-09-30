Now instead of simply printing a line that says "Telling my agents to do something"...

Let's add in some code provided by the team at CrewAI...

We could use only one file for writing all the code of our project BUT that is not advised as it would cause us to constantly be scrolling back and forth as we add more lines

THEREFORE, just so this `main.py` file doesn't get bloated let's create another file called `crew.py`...

```
touch src/our_crew_of_agents/crew.py
```

and paste in this code that I pieced together by looking at various examples in the CrewAI examples repo...

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

we can call this code in the `crew.py` file from the `main.py` file like this...

```update src/our_crew_of_agents/main.py
from src.our_crew_of_agents.crew import OurCrewOfAgents

print("Calling our crew of agents...")
OurCrewOfAgents().crew().kickoff()
```

(PAUSE)

Remember in our Dockerfile how it included a line specifying the PYTHONPATH aka `ENV PYTHONPATH=/code`

This line configures the Python intepreter on our Dev container to look for code we import throughout our project at the specified location.

The complete path to the `crew.py` file is `/code/src/our_crew_of_agents/crew.py`

I know, in the Python code dots are being used instead of slashes to specify the path but in this context it means the same thing...

And also note that when performing imports, we DON'T have to write `.py` at the end the filenames

OK SHORT SIDE NOTE

You might run into and issue where your VSCode editor can't find the Python intepreter on the Dev container

