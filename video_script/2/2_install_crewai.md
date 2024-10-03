## Install the crewai CLI

Now that we have a solid foundation, let's install `crewai` from the Python Package Index (aka PyPI) like so...

- `pip install crewai==0.63.6`

## Scaffold the crew

And after installing `crewai` on our Dev Container, we can use the CrewAI CLI like so...

- `creawai --help`
- `crewai create crew <project_name>`

In this DEMO we're going to be creating a group of acclaimed musicians to help us write a hit song...

So let's call this project `hit_music_only` and enter `crewai create crew hit_music_only`

## Take a look at the generated files

- We can see on the command line the list of all the files and folders that were created for us...
  - This is great because we don't have to create all these files and folders manually

## Restructuring scaffolded project

- Also, we can see the CrewAI CLI created a project for us within a folder called `hit_music_only`

- & NOTE 2 things:

  1. these generated files follow the guidelines of the Python Poetry framework
    - Poetry, for those who don't know, is a popular way of organizing Python code that has gained a lot of traction over the past few years...
  2. the content of these files includes code for a crew consisting of 2 agents: a "Research" agent and an "Analyst" agent

- OK! So because `crewai` generated this `hit_music_only` project into a subfolder of the project root and not the project root itself, we have to make a little adjustment that will make sense in a moment...

- All we have to do to make this adjustment is update the "workspaceFolder" key in our `devcontainer.json` config

```
"workspaceFolder": "/code/hit_music_only",
```

- Because this little adjustment required a change to the configuration of the Dev container itself, we have to now rebuild it...

- AS A REMINDER, the configuration of our Dev container is defined by the content of the devcontainer.json and the Dockerfile.dev files from STEP 1

- There are a couple of ways we can perform the rebuild but we'll do it like this for simplicity...

- Let's just close our the Dev container and then reopen it...

- This is how we reopen it. We open the folder containing our project with VSCode just like we would open any other project folder and because we placed a `devcontainer.json` file in the appropriate place, VSCode, courtesy of the "Dev Containers" extension, will detect that we would like to launch a Dev container.

- We can trigger the rebuild by clicking this button in the popover OR by using the command palette

- Let's just use the command palette in case you don't see this pop up on your side for some reason!

- Type SHIFT + COMMAND + P to open the command palette and select the option
  - `Dev Containers: Rebuild Container`

## Examining the Dev container after re-opening

- So now after relaunching the Dev container, we see we're in the generated CrewAI Python Poetry project and NOT our project root : )
- If I type `pwd` into the terminal connected to the Dev container you can see that this is indeed true
- Problem solved...
- So now when we open this CrewAI project in our Dev container, VSCode will detect it's a Python Poetry project and will enable some extra nice-to-have features (like coloring our code & allowing us to inspect imports) that should improve our development experience...

## Dev containers can lose state

- Also check this out: if I type `creawai --help` [`crewai` not found]
- This is because when we rebuilt our Dev container, it lost it's state
- You can shut down the Dev container whenever you like and it's state will be preserved BUT if you rebuild it, it will lose it's state
- So we have to now reinstall `crewai`
- `pip install crewai==0.63.6`

## FYI, 

- IF we want to avoid reinstalling the CrewAI CLI each time we rebuild the Dev container, we can add an additional line to the Dockerfile.dev to give us a container with Python AND the CrewAI CLI installed when launching...

BUT let's not worry about that for now and move forward...

```.Dockerfile.dev
FROM python:3.12-slim
RUN apt-get update && apt-get install -y build-essential
RUN pip install --no-cache-dir crewai==0.63.6
```


## Python Poetry projects require us to run an installation process before running

- We're almost ready to run this crew provided to us by the CrewAI cli but we have to do one last thing

- Because the generated CrewAI project is based on Python Poetry, we have to run the standard Poetry setup process by entering the following command...
- `poetry install` or `poetry install -vvv`
- Let's time this to see how long it takes...
- WOW! That took a while (like 5 minutes for me)
- I think the Poetry project setup took so long because this generated CrewAI project comes with tools and CrewAI seems to have many. For example, on CrewAI's website I'm seeing tools for interacting with databases, scraping websites, searching YouTube, etc.

(LOOK CAMERA)

- FYI: If you're not familiar with the term "tools" in the context of Agents, tools are the integrations made between our Agents and the outside world

## Run the crew

- Ok! Now let's try running our generated CrewAI project with the CrewAI CLI and see what happens...
- Let's enter: `crewai run` 
- And believe it or not, despite this error we're looking good :)

## We're still getting some errors but we're making progress

- This error is happening because we haven't added an OPENAI_API_KEY key to our project

- CrewAI supports various LLMs for powering the agents in a crew but by default is set up to use OpenAI

- Before we move on to the next section and add in our OPENAI_API_KEY, let's recap what's happened up to this point...

## RECAP

1. First we started from scratch (aka an empty folder)

2. We then set up a Dev container (which is like a mini-machine that runs on top of our laptop or Desktop or whatever we're using)

3. Then we installed the `crewai` package from PyPI in order to use the CrewAI CLI

4. Then we generated a CrewAI project called `hit_music_only`

5. Then we noticed how the generated project was placed into a subfolder AND because we wanted our VSCode editor to play well with this generated Poetry-based project we had to adjust the configuration of our Dev container to open the generated subfolder when launching...

6. So we edited the `devcontainer.json` config and rebuilt our Dev container

7. After the new Dev container finished launching, we were placed directly into the generated CrewAI Poetry project which allowed VSCode to give us some extra nice-to-have development features like import inspection, and syntax highlighting, etc.

8. Then, because our Dev container lost it's state after being killed, we had to reinstall the `crewai` package

9. We then ran the standard Poetry setup process aka "poetry install"

10. And after the poetry setup process completed, we ran our CrewAI project and succesfully launched the crew of default agents before they errored out due to "missing access credentials" when trying to connect to OpenAI

I hope this makes sense : )

Let's move forward by adding an OPENAI_API_KEY to our project