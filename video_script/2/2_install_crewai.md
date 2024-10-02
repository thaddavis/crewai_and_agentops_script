## Install the crewai CLI

Now that we have a solid development environment to build on top of, let's install `crewai` from the Python Package Index (aka PyPI) like so...

- `pip install crewai==0.63.6`

## Scaffold the crew

And after installing `crewai` on our "mini-machine" or Dev Container, we can use the CrewAI CLI like so...

- `creawai --help`
- `crewai create crew <project_name>`

In this DEMO we're going to be creating a group of acclaimed musicians to help us write a hit song...

So let's call this project `hit_music` and enter `crewai create crew hit_music`

## Take a look at the generated files

- We can see on the command line the list of all the files and folders that were created for us...
  - This is great because we don't have to create all these files and folders manually

## Restructuring scaffolded project

- Also, we can see the CrewAI CLI created a project for us within a folder called `hit_music`

- Note 2 things:

  1. these generated files follow the guidelines of the Python Poetry framework
    - Poetry, for those who don't know, is a popular way of organizing Python code that has gained a lot of traction over the past few years...
  2. the content of these files includes the code for a crew consisting of 2 agents: a "Research" agent and an "Analyst" agent

- OK! So because `crewai` generated this `hit_music` project into a subfolder of the project and not the project folder itself, we have to make a little adjustment that will make sense in a moment...

- All we have to do to make this minor adjustment is update the "workspaceFolder" key in our `devcontainer.json` config

```
"workspaceFolder": "/code/hit_music",
```

- VSCode has a process it runs when launching where it tries to detect the type of project being opened (in our case a Python Poetry project) and enable extra features like coloring our code, allowing us to inspect imports, etc.

- Because this little adjustment required a change to the configuration of the "mini-machine" aka the devcontainer itself, we have to now rebuild it...

- FYI: as a reminder, the configuration of our Dev container is defined by the content of the devcontainer.json file and the Dockerfile.dev file from STEP 1

- There are a couple of ways we can perform the Dev container rebuild but we'll just do it like this for simplicity...

- Let's just close our our Dev container and then reopen it...

- This is how we reopen it. We open the folder containing our project with VSCode on our base machine, aka open the folder just like we would open any other project folder with VSCode.

- And note how because we placed a `devcontainer.json` file in the appropriate place, VSCode, courtesy of the "Dev Containers" extension, detected that we would like to launch a Dev container.

- We can trigger the rebuild from this little toast by clicking this button in the toast OR by using the command palette

- Let's use the command palette in case you don't see this pop up / toast menu on your side when following along for some reason!

Let's type SHIFT + COMMAND + P to open the command palette and select the option
  - `Dev Containers: Rebuild Container`

## Examining the Devcontainer after re-opening

- Now after relaunching the Dev container, we see we're in the generated CrewAI Python Poetry project and NOT our project root : )
- If I type `pwd` into the terminal connected to the Dev container you can see that this is indeed true
- Problem solved...
- Now when we open this CrewAI project in our Dev container, VSCode will detect it's a Python Poetry project and will enable some extra nice-to-have features that should improve our development experience...

## Devcontainer can lose it's state

- - `creawai --help` [`crewai` not found]
- ALSO NOTE THE EVEN THOUGH WE INSTALL CREWAI BEFORE THE CREWAI CLI IS NOWHERE TO BE FOUND!
- This is because when we rebuilt our Dev container, it lost it's state
- You can shut down the Dev container whenever you like and it's state will be preserved BUT if you rebuild it, it CAN lose it's state depending on the details...
- So we have to now reinstall `crewai`
- `pip install crewai==0.63.6`

## FYI, 

- IF we want to avoid reinstalling the CrewAI CLI each time we rebuild the Dev container, we can add an additional line to the Dockerfile.dev to give us a Dev container with Python AND the CrewAI CLI installed when launching...

BUT let's not worry about that for now and move forward...

```.Dockerfile.dev
FROM python:3.12-slim
RUN apt-get update && apt-get install -y build-essential
RUN pip install --no-cache-dir crewai==0.63.6
```


## Python Poetry projects require us to run an installation process before running

- We're almost ready to run this crew provided to us by the CrewAI cli but we have to do one last thing

- Because the generated CrewAI project is based on Python Poetry, we have to first run the standard Poetry setup process by entering the following command...
- `poetry install` or `poetry install -vvv`
- Let's time this to see how long it takes...
- WOW! That took a while (like 5 minutes for me)
- I think the installation took so long because this generated CrewAI project is set up to support tools and CrewAI seems to have many tools. For example, on CrewAI's website I'm seeing tools for interacting with databases, scraping websites, searching YouTube, etc.

(LOOK CAMERA)

- FYI: If you're not familiar with the term "tools" in the context of LLM agents, tools are the integrations made between our Agents and the outside world

## OK! Now let's try running our generated CrewAI project now with the CrewAI CLI and see what happens...

- Ok NOW we can run our crew...
- Let's enter: `crewai run` 
- And believe it or not we are looking good :)

## We're still getting some errors but we're making progress

- This next error is happening because we haven't added an OPENAI_API_KEY key to our project

- CrewAI supports various LLMs for powering the agents in a crew but by default is set up to use OpenAI

- Before we add in our OPENAI_API_KEY, let's recap what's happened up to this point

## RECAP

1. First we started from scratch (aka an empty folder)

2. We then set up a Dev container (which is like a mini-machine that runs on top of our laptop or Desktop or whatever we're using)

3. Then we installed the `crewai` package from PyPI in order to use the CrewAI CLI

4. Then we generated a CrewAI project called `hit_music`

5. Then we noticed how the generated project was placed into a subfolder AND because we wanted our VSCode editor to play well with this generated Poetry-based project we had to adjust the configuration of our Dev container to open the generated subfolder when launching...

6. So we edited the `devcontainer.json` config and rebuilt our Dev container

7. After the new Dev container finished launching, we were placed directly into the generated CrewAI Poetry project which allowed VSCode to give us some extra nice-to-have development features like import inspection, and syntax highlighting, etc.

8. Then, because our Dev container lost it's state after being killed, we had to reinstall the `crewai` package to continue using the CrewAI CLI

9. We then ran the standard Poetry framework initial setup process "poetry install"

10. After the poetry installation process completed, we ran our CrewAI project and succesfully launched the crew of default agents before they errored out due to missing access credentials when trying to connect to OpenAI

I hope this makes sense : )

Let's now move forward by adding an OPENAI_API_KEY to our project