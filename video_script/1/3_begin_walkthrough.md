# FIRST APPROACH

https://docs.crewai.com/getting-started/Start-a-New-CrewAI-Project-Template-Method/#creating-a-new-project

Let's create the following files & folders in the Dev container...

```
mkdir -p src/our_crew_of_agents
touch src/our_crew_of_agents/main.py 
```

When a file name ends in `.py` it indicates to us that it will hold Python code...

<!--
In Python projects, you'll often see a file called "main.py"

In this video, `main.py` will be the file we run to launch our agents and give them tasks

For the beginners watching, it's important to tell you that when programming, we can call files, folders, and most other aspects of the code we write whatever we like.

For example, we could've name this file blah.py`

```
mv src/our_crew_of_agents/main.py src/our_crew_of_agents/blah.py
print("Telling my agents to do something...")
python blah.py
```

For the beginners, names are just labels and there are an infinite number of ways to label and organize code in a project.

In practice tho, so it's easier to collaborate and build with others, we follow conventions.

And these conventions, or standard practices, are learned over time through experience. So be patient if you feel unfamiliar with what you're seeing...

Watch the whole video and come back to any confusing parts later...
-->

So let's rename blah.py back to main.py as that is more conventional...

And make sure everything works...

`mv src/our_crew_of_agents/blah.py src/our_crew_of_agents/main.py`

TEST: `python src/our_crew_of_agents/main.py` √

And everything works just the same...
