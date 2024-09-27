# FIRST APPROACH

https://docs.crewai.com/getting-started/Start-a-New-CrewAI-Project-Template-Method/#creating-a-new-project

First, let's create the following files & folders...

```
mkdir -p src/our_crew_of_agents
touch src/our_crew_of_agents/main.py 
```

When a file name ends in `.py` it indicates to us that it holds Python code...

<!--
In Python projects, you'll often see a file called "main.py"

In this walkthrough, `main.py` will be the file we run to launch our CrewAI project which will contain code (or instructions) for running a group of agents...

For the beginners watching, it's important to tell you that when programming, we can call files, folders, and many aspect of the code we write whatever we like.

For example, we could name this file that launches our application `blah.py`

```
mv src/our_crew_of_agents/main.py src/our_crew_of_agents/blah.py
print("Tell my crew of agents to do something")
python blah.py
```

Right?

Names are just labels. So there are an infinite number of ways to organize code in a project. In practice tho, so easy for us collectively to understand, collaborate, and build together, we follow conventions.

These conventions are learned over time through experience and through working with others so be patient if you feel unfamiliar with what you're seeing...
-->

Let's rename blah.py back to main.py as that is more conventional...

And make sure everything works...

`mv src/our_crew_of_agents/blah.py src/our_crew_of_agents/main.py`

TEST: `python src/our_crew_of_agents/main.py` √

And everything works just the same...
