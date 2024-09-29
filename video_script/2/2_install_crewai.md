## Install the crewai CLI

Now that we have a solid development environment to build on top of, let's install `crewai` like so...

- `pip install crewai==0.63.6`

## Scaffold the crew

After installing `crewai` on our "mini-machine" or Dev Container, we can use it

CrewAI comes with a handy tool for generating projects called the CrewAI CLI

The way you use the CrewAI CLI is like so...

- `crewai create crew <project_name>`

In this DEMO we're going to be creating a group of acclaimed musicians to help us write a hit song...

So I'll call this project `hit_music`

- So let's type `crewai create crew hit_music` and see what happens...

## Take a look at the generated files

- We can see on the command line the list of all the files and folders that were created for us...
- This is great because we don't have to create all these files and folders manually ourselves

## Restructuring scaffolded project

- OK! This next minute or so is going to be an amazing crash course in Python for the beginners watching so relax and focus in. If you feel lost, just watch through to the end of the video and come back to any confusing parts...

- We can see that the CrewAI CLI created a CrewAI project for us within a subfolder called `hit_music` and looking closely at the generated files inside, we can see that this is a `Python Poetry` project

- Poetry, for those who don't know, is a popular way of organizing your Python code that has gained a lot of traction over the past few years...

- If we look even closer, we can also see that this generated project comes with a default crew consisting of a "Research" agent and an "Analyst" agent

- Because `crewai` generated this `hit_music` project into a subfolder we have to make a minor adjustment that will make sense in a moment...

- All we have to do to make this minor adjustment is update the "workspaceFolder" key in our `devcontainer.json` config

```
"workspaceFolder": "/code/hit_music",
```

- VSCode has a process it runs when launching where it tries to detect the type of project being opened (in our current case a Python Poetry project) and enable extra features like coloring our code, allowing us to inspect imports, etc.

- Because we updated the configuration of our "mini-machine" or Devcontainer we have to now rebuild it...
- The configuration of our Dev container is defined by the devcontainer.json file and the Dockerfile.dev file

- There are a couple of ways we can do the rebuild but we'll just do it like this for now...

- We will close our our Devcontainer and then reopen it.

- This is how we reopen it. We open the folder representing the root of our project with VSCode, just like we would with any other coding project. And because we placed a devcontainer.json file in the appropriate place, VSCode, courtesy of the "Dev Containers" extension, will detect that we would like to possibly launch a Devcontainer.

- We can trigger the rebuild from this pop up OR use the command palette

- Let's use the command palette in case you don't see a pop up on your side in case you're following along!

SHIFT + COMMAND + P
  - `Dev Containers: Rebuild Container`

## Examining the Devcontainer after re-opening

- Now we see we are in the generated CrewAI project folder and NOT our project root : )
- If I type `pwd` into the terminal connected to the Dev container you can see this is indeed true
- Problem solved...
- Now when we open this CrewAI project in our Dev container, VSCode will detect that it's a Python Poetry project and will enable some nice-to-have features that should improve our development experience

## Devcontainer can lose it's state

- OK!
- Because we killed and then rebuilt our Devcontainer, it lost it's state
- So we have to now reinstall `crewai`
- `pip install crewai==0.63.6`
- Now we have the CrewAI CLI available to us again

## FYI, 

- If we want to avoid reinstalling the CrewAI CLI each time we rebuild the Dev container, we can add an additional line to Dockerfile.dev to give us "mini-machine" with Python AND the CrewAI CLI when launching

BUT let's not worry about that for now...

```.Dockerfile.dev
FROM python:3.12-slim
RUN apt-get update && apt-get install -y build-essential
RUN pip install --no-cache-dir crewai==0.63.6
```


## Python Poetry projects require us to run an installation process before running

- We're almost ready to run this crew provided to us by the CrewAI cli but we have to do one last thing

- Because the generated CrewAI project is based on Python Poetry we have to first run the standard Poetry setup process by entering the following command...
- `poetry install` or `poetry install -vvv`
- Let's time this to see how long it takes...
- WOW! That took a while (like 5 minutes for me)
- I think the installation took so long because this generated CrewAI project is set up by default to support tools and CrewAI seems to have many tools. For example, on CrewAI's website I'm seeing ones for interacting with databases, scraping websites, searching YouTube, etc.
- FYI: If you're not familiar with the term "tools" in the context of LLM agents, tools are the integrations made between our Agents and the outside world

## OK! Now let's try running our generated CrewAI project now with the CrewAI CLI and see what happens...

- Ok NOW we can run our crew...
- crewai run 
- Looking good :)

## We're still getting some errors but we're making progress

- This next error is happening because we haven't added an OPENAI_API_KEY key to our project

- CrewAI supports various LLMs for powering the agents in a crew but by default is set up to use OpenAI

- Before we add in our OPENAI_API_KEY and wrap this up, let's recap what's happened up to this point

## RECAP

1. First we started from scratch (aka an empty folder)

2. Then we set up a Devcontainer (which is a mini-machine that runs on top of our laptop or Desktop or whatever we're using)

3. Then we installed the `crewai` package from PyPi in order to use the CrewAI CLI

4. Then we generated a project called `hit_music` as we are planning to build a crew of agents specialized in writing hit songs

5. Then we noticed how the CrewAI CLI generated a project into a subfolder AND because we wanted our VSCode editor to play well with this CrewAI Poetry framework based project we had to adjust the configuration of our Devcontainer to open the generated subfolder when launching...

6. So we edited the `devcontainer.json` config and rebuilt our Devcontainer

7. After the new Devcontainer finished launching, we were placed directly into the generated CrewAI project which allowed VSCode to detect that our project was Python Poetry based which will give us some extra nice-to-have development features like import inspection, and syntax highlighting, etc.

8. Because our mini-machine lost it's state after being killed, we had to then reinstall the `crewai` package to continue using the CrewAI CLI

9. We were then just about ready to run our generated crew, BUT!, because the generated project was based on the Python Poetry framework we had to run the standard "poetry install" process to set it up

10. After the poetry installation process completed, we ran our CrewAI project and succesfully launched the crew of default agents before they errored out due to missing access credentials when trying to connect to OpenAI

I hope you're following : )

Let's now move forward by adding an OPENAI_API_KEY to our project