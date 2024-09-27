## Let's try running our crew again

- `python src/crew_of_agents/main.py`

## Observe the error

- FileNotFoundError: [Errno 2] No such file or directory: '/code/src/crew_of_agents/config/tasks.yaml'

- OK! As we see, the way CrewAI is designed requires us to specify a file called `tasks.yaml` that outlines what we want the agents in our crew to do...

- So let's create a file called `tasks.yaml`

- https://docs.crewai.com/getting-started/Start-a-New-CrewAI-Project-Template-Method/#tasksyaml
- `touch src/crew_of_agents/config/tasks.yaml`
```
write_declaration:
    description: >
      Write the Declaration of Independence for the United States.
    expected_output: >
      The Declaration of Independence that will be sent to the British government.
    agent: thomas_jefferson

military_strategy:
    description: >
      Generate a military strategy to defeat the British Army.
    expected_output: >
      A detailed military strategy that will lead to victory in the Revolutionary War.
    agent: george_washington
```

- AND this is how we let our crew know about the tasks we would like it to perform... 
- add tasks to the `crew.py` file

```.py
@task
	def write_declaration(self):
		return Task(
    	config=self.tasks_config["write_declaration"],
    )
@task
	def military_strategy(self):
		return Task(
    	config=self.tasks_config["military_strategy"],
    )
```