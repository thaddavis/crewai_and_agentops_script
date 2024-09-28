## Install the crewai CLI

Now that we have a solid development environment to build on top of let's install crewai like so...

- `pip install crewai==0.63.6`

## Scaffold the crew

After installing `crewai` on our "mini-machine", we can use it

CrewAI comes with a handy tool for generating projects called the CrewAI CLI

The way you use the CrewAI CLI is like so...

- `crewai create crew <project_name>`

In this walkthrough we are going to be creating a group of acclaimed songwriters and producers to help us write a hit song...

So I'll call this project `hit_music_crew`

- `crewai create crew hit_music_crew`

## Take a look at the generated files

- We can see on the command line the list of all the files created for us...
- and this is great because we don't have to create all these files and folder ourselves
- And my understanding is that this project structure is also compatible with some of the more advanced features of CrewAI's platform, like for example training and hosting...

- I've never testing these advanced features of CrewAI's platform but my understanding is ease of access to them is an added benefit of using the CrewAI CLI for scaffolding your multi-agent projects

## Restructuring scaffolded project

- This next minute or so is going to be an amazing crash course in Python for the beginners watching so relax and focus in. If you feel lost after a minute or two just rewind and watch this part again before continuing...

- We can see that the CrewAI CLI created a CrewAI project within a subfolder called `hit_music_crew` and judging by the generated files inside my experience tells me this is a `Python Poetry` project

- And if we look closer we see this generated project also comes with a default crew consisting of a "Researcher" and an "Analyst"

- Poetry, for those who don't know, is a popular framework for organizing your Python code that has gained a lot of traction over the past few years...

- OK! So this next point is going to be interesting. VSCode, our editor, has a process it runs when launching whereby it tries to detect the type of project being opened

- Because the CrewAI CLI generated the project into a subfolder it's going to throw off this VSCode launch process

- BUT! Luckily, fixing it is easy...

- All we have to do to fix this minor issue is update the "workspaceFolder" key in our `devcontainer.json` configuration

```
"workspaceFolder": "/code/hit_music_crew",
```

- Now when we open our Devcontainer it'll open the folder holding the generated project and enable all the nice-to-have features that VSCode supports when working with Python projects

- Each time we update our Devcontainer configuration we have to rebuild it like so...
- There are a couple of ways we can rebuild it but we'll do it like this for now...

- We will close our "mini-machine" aka our Devcontainer and then reopen it.

- This is how we reopen it. We open the folder container representing the root of our project with VSCode just like we would any other project. And because we have placed a devcontainer.json file in the appropriate place, VSCode will detect that we would like to launch a Devcontainer.

- We can trigger the rebuild from this pop up OR use the command palette

- Let's use the command palette in case you don't see a pop up on your side if you are following along!

SHIFT + COMMAND + P
  - `Dev Containers: Rebuild Container`

## Examining the Devcontainer after re-opening

- Now we see we are in the generated CrewAI project and not our project root : )
- `pwd`

## Devcontainer can lose it's state

- OK!
- Each time you kill or rebuild a Devcontainer it loses it's state
- And because we rebuilt our Devcontainer we have to now reinstall `crewai`
- `pip install crewai==0.63.6`

## Python Poetry projects require us to run an installation process before running

- We mentioned that the generated CrewAI project is based on Python Poetry so before we can run it we have to first run the standard Poetry installation process
- `poetry install -vvv`
- WOW! That took a while (like 5 minutes for me)
- I think installation took so long because this generated project is set up by default to support tool usage and CrewAI seems to support many tools. I'm seeing ones for interacting with databases, scraping websites, & searching YouTube, etc.
- FYI: If you're not familiar with the term "tools" in the context of Agent development, tools are the integrations made between our Agents and the outside world

## OK! Now let's try running our generated CrewAI project now with the CLI and see what happens...

- crewai run 
- Looking good :)

## Still getting errors but we are making progress

- This next error looks like it's because we haven't added an OpenAI API key to our project

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

4. Then we generated a project called `hit_music_crew` as we are planning to build a crew of agents specialized in writing hit songs

5. Then we noticed how the CrewAI CLI generated a project into a subfolder AND because we wanted our editor VSCode to play well with this CrewAI project we had to adjust the configuration of our Devcontainer to open the subfolder when launching

6. So we edited the `devcontainer.json` config and then rebuilt our Devcontainer

7. After we had our new Devcontainer, we had to reinstall the `crewai` package because Devcontainers lose their state after being killed or rebuilt

8. After the new container launched we were placed directly into the generated CrewAI project which allowed VSCode to detect that our project was Python-based whic gives us some extra nice-to-have dev features like import inspection, and syntax highlighting, etc.

9. Because the generated project was based on the Python Poetry framework we had to run the standard `poetry install -vvv` process

10. After the poetry installation process completed, we ran our CrewAI project and were able to succesfully launch the crew of default agents before they errored out due to missing access credentials when connecting to OpenAI

If you feel lost, rewatch this part once again before continuing

and when you're ready, let's move forward by adding an OPEN_API_KEY to our project