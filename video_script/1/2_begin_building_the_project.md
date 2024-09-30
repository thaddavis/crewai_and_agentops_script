Now that we have a solid foundation...

We can start building our CrewAI project

The way we're going to build this project is NOT the recommended way to do this at all

BUT for the purpose of learning how CrewAI works it will be great...

What we're going to do is build a simple a CrewAI project up from scratch one file at a time

(PAUSE)

# FIRST APPROACH

Here on CrewAI's documentation they provide an outline of what a CrewAI application looks like so let's take a look...

we see blah, we see blah...

https://docs.crewai.com/getting-started/Start-a-New-CrewAI-Project-Template-Method/#creating-a-new-project

OK!, So in the same way a chef can look at a recipe and get the gist of it and then improvise on it when their cooking a dish, we are going to build a CrewAI application based on this general project structure...

https://docs.crewai.com/getting-started/Start-a-New-CrewAI-Project-Template-Method/#creating-a-new-project

Let's create the following file & folders in the Dev container...

```
mkdir -p src/our_crew_of_agents
touch src/our_crew_of_agents/main.py
```

<!--
When a file name ends in `.py` it indicates to us that it will hold Python code...

In Python projects, it's typical to see a file called "main.py"

In this walkthrough, `main.py` will be the file we run to launch our crew of agents and give them tasks

For the beginners watching, it's important to tell you that when programming, we can call files, folders, and most other aspects of the code we write whatever we like.

For example, we could've name this `main.py` file `blah.py`

```
mv src/our_crew_of_agents/main.py src/our_crew_of_agents/blah.py
print("Telling my agents to do something...")
python src/our_crew_of_agents/blah.py
```

(PAUSE)

Names are just labels and there are an infinite number of ways to label and organize code in a project.

In practice tho, so it's easier to collaborate and build with others we follow conventions.

These conventions, or standard practices, are learned over time through experience so be patient if you feel unfamiliar with what you're seeing...

Watch the whole video and come back to any confusing parts later...
-->

Let's rename blah.py back to main.py as that is more conventional...

And make sure everything still works...

`mv src/our_crew_of_agents/blah.py src/our_crew_of_agents/main.py`

TEST: `python src/our_crew_of_agents/main.py` √

And everything works just the same...
