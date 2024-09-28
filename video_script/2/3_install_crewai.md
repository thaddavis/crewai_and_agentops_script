## Install the crewai CLI

Now that we have a solid development environment to build on top of, let's install `crewai` like so...

- `pip install crewai==0.63.6`

## Scaffold the crew

After installing `crewai` on our "mini-machine" or Dev Container, we can use it

CrewAI comes with a handy tool for generating projects called the CrewAI CLI

The way you use the CrewAI CLI is like so...

- `crewai create crew <project_name>`

In this walkthrough we're going to be creating a group of acclaimed musicians to help us write a hit song...

So I'll call this project `hit_music`

- So when we type `crewai create crew hit_music` let's see what happens...

## Take a look at the generated files

- We can see on the command line the list of all the files and folders created for us...
- This is great because we don't have to create all these files and folders manually ourselves

## Restructuring scaffolded project

- OK! This next minute or so is going to be an amazing crash course in Python for the beginners watching so relax and focus in. If you feel lost, just watch through to the end of the video and come back to any confusing parts...

- We can see that the CrewAI CLI created a CrewAI project within a subfolder called `hit_music` and looking closely at the generated files inside we can see that this is a `Python Poetry` project

- Poetry, for those who don't know, is a popular way of organizing your Python code that has gained a lot of traction over the past few years...

- If we look even closer, we also see this generated project comes with a default crew consisting of a "Researcher" agent and an "Analyst" agent

- Because `crewai` generated the project into a subfolder we have to make a minor adjustment that will make sense in a moment...

- All we have to do to make this minor adjustment is update the "workspaceFolder" key in our `devcontainer.json` configuration

```
"workspaceFolder": "/code/hit_music",
```

- VSCode has a process it runs when launching whereby it tries to detect the type of project being opened (in our current case a Python Poetry project) and enable extra features like coloring our code, allowing us to inspect imports etc.

- Because we updated the configuration of our "mini-machine" or Devcontainer we have to now rebuild it...
- There are a couple of ways we can rebuild it but we'll do it like this for now...

- We will close our "mini-machine" aka our Devcontainer and then reopen it.

- This is how we reopen it. We open the folder representing the root of our project with VSCode just like we would with any other coding project. And because we've placed a devcontainer.json file in the appropriate place, VSCode, courtesy of the "Dev Containers" extension, will detect that we would like to possibly launch a Devcontainer.

- We can trigger the rebuild from this pop up OR use the command palette

- Let's use the command palette in case you don't see a pop up on your side IF you're following along!

SHIFT + COMMAND + P
  - `Dev Containers: Rebuild Container`

## Examining the Devcontainer after re-opening

- Now we see we are in the generated CrewAI project and not our project root : )
- `pwd`
- Problem solved...

## Devcontainer can lose it's state

- OK!
- Each time you kill or rebuild a Devcontainer it loses it's state
- So because we rebuilt our Devcontainer we have to now reinstall `crewai`
- `pip install crewai==0.63.6`

## Python Poetry projects require us to run an installation process before running

- We mentioned that the generated CrewAI project is based on Python Poetry so before we can run it we have to first run the standard Poetry installation process
- `poetry install -vvv`
- WOW! That took a while (like 5 minutes for me)
- I think the installation took so long because this generated project is set up by default to support tool usage and CrewAI seems to support many tools. I'm seeing ones for interacting with databases, scraping websites, & searching YouTube, etc.
- FYI: If you're not familiar with the term "tools" in the context of LLM Agent development, tools are the integrations made between our Agents and the outside world

## OK! Now let's try running our generated CrewAI project now with the CrewAI CLI and see what happens...

- crewai run 
- Looking good :)

## We're still getting some errors but we're making progress

- This next error looks like it's because we haven't added an OPENAI_API_KEY key to our project

- CrewAI supports various LLMs for powering the agents in a crew but by default is set up to use OpenAI

```
litellm.exceptions.AuthenticationError: litellm.AuthenticationError: AuthenticationError: OpenAIException - Error code: 401 - {'error': {'message': 'Incorrect API key provided: YOUR_API_KEY. You can find your API key at https://platform.openai.com/account/api-keys.', 'type': 'invalid_request_error', 'param': None, 'code': 'invalid_api_key'}}
An error occurred while running the crew: Command '['poetry', 'run', 'run_crew']' returned non-zero exit status 1.
```

- Before we add in our OPENAI_API_KEY and move on tho let's recap what has happened up till this point

## RECAP

1. First we started from scratch (aka an empty folder)

2. Then we set up a Devcontainer (which is a mini-machine that runs on top of our base machine)

3. Then we installed the `crewai` package from PyPi in order to gain access to the CrewAI CLI

4. Then we generated a project called `hit_music` as we are planning to build a crew of agents specialized in writing hit songs

5. Then we noticed how the CrewAI CLI generated a project into a subfolder AND because we wanted our VSCode editor to play well with this CrewAI project we had to adjust the configuration of our Devcontainer to open this generated subfolder when launching...

6. So we edited the `devcontainer.json` config and then rebuilt our Devcontainer

7. After we had our new Devcontainer, we had to reinstall the `crewai` package because Devcontainers lose their state after being killed or rebuilt

8. After the new container launched, we were placed directly into the generated CrewAI project which allowed VSCode to detect that our project was Python Poetry based which gives us some extra nice-to-have development features like import inspection, and syntax highlighting, etc.

9. Because the generated project was based on the Python Poetry framework we had to run the standard `poetry install -vvv` process to set it up

10. And after the poetry installation process completed, we ran our CrewAI project and succesfully launched the crew of default agents before they errored out due to missing access credentials when connecting to OpenAI


Let's now move forward by adding an OPEN_API_KEY to our project