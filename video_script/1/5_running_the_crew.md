## Let's try running our crew

- `python src/our_crew_of_agents/main.py`

Whengh, Whengh, Wheowgh...

I'm intentionally showing these errors so you get a feel for how this stuff really works

## Importing `crewai`

So when we ran the `main.py` file our computer start reading the code (aka our instructions) from top to bottom and when we got to this line we jumped over to the crew.py file and started reading the instructions over here...

BUT inside of this `crew.py` file you see we're importing `crewai`

The same way that we jumped from the `main.py` file over to the `crew.py` file, *when* the python interpreter gets to *this* point in our program, it needs to jump from the `crew.py` over to the code in some file provided by `crewai`

So now your understand the last error.

This error is telling us that `crewai` was nowhere to be found on our "mini-machine" aka our Dev container

So we need to add "crewai" to our Dev container...

Python has a system called PyPi [https://pypi.org/] (which is short for Python Package Index) that allows us to easily download code published by other members of the Python community

So if we enter this instruction...

- `pip install crewai==0.65.2`

all of the Python code published to PyPi by the CrewAI team will be downloaded onto our "mini-machine"

- Notice how I'm including the specific version of `crewai` so you know exactly what I'm using in case your wondering

- Omitting the version number and typing just `pip install crewai` will download the latest version to your computer

- IF you're following along just download the version I'm using if you're unsure of what to do...

- Installing `crewai` worked √

## Let's run our crew again...

- So let's run our project again and see what happens

- `python src/our_crew_of_agents/main.py`

- Ok we see something new which is great. That means we fixed the `crewai` import error

## Observe the error

- FileNotFoundError: [Errno 2] No such file or directory: '/code/src/our_crew_of_agents/config/agents.yaml'

- I wonder what this could mean...

Dun, Dun, Dun...

SOUND EFFECT: https://www.youtube.com/watch?v=E6iwa12fGR0