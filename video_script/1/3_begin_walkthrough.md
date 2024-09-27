# FIRST APPROACH

https://docs.crewai.com/getting-started/Start-a-New-CrewAI-Project-Template-Method/#creating-a-new-project

First, let's create the following files & folders...

```
mkdir -p src/crew_of_agents
touch src/crew_of_agents/main.py 
```

<!--
Often when looking at a coding project, you'll see a file called something along the lines of "main"

In this walkthrough, `main.py` will be the file we run to launch our project which will contain code (or instructions) for running a group of Agents...

Keep in mind, that we can call files, folders, and code snippets whatever we like when coding for example `blah.py`

<mini blah.py DEMO>

Names are just labels BUT! JUST SO it's easy for others to understand, collaborate, and build on top of our code, we follow conventions and these conventions you learn over time by working with others...
-->

```inside src/crew_of_agents/main.py let's place the following code
print("Run a crew of agents...")
```

TEST: `python src/crew_of_agents/main.py` √