OK! Now instead of simply printing a line that says "Run a crew of agents...", let's do something more interesting...

Let's import some of the official code provided by CrewAI and call it from our `main.py` script...

When building an application we could include all the related code in one file BUT that gets hectic as you are constantly scrolling looking for things when ready it...

THEREFORE, so our main file doesn't get bloated with too many lines let's create another file...

```
touch src/crew_of_agents/crew.py
```

Now let's add the following code that I pieced together by looking at various examples provided by CrewAI...

https://github.com/crewAIInc/crewAI-examples/blob/main/marketing_strategy/src/marketing_posts/crew.py

```add to src/crew_of_agents/crew.py
from crewai import Crew, Process
from crewai.project import CrewBase, agent, crew

@CrewBase
class CrewOfAgents():
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

```update src/crew_of_agents/main.py
from src.crew_of_agents.crew import CrewOfAgents

print("Calling the CrewOfAgents...")
CrewOfAgents().crew().kickoff()
```