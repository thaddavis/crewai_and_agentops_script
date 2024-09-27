## Try running our crew

- `python src/our_crew_of_agents/main.py`

Whengh, Whengh, Wheowgh...

## Importing `crewai`

We imported `crew.py` from the `main.py` and that worked because the `ENV PYTHONPATH=/code` instruction told Python the base point of where to look...

But inside of this `crew.py` file we imported `crewai`

The same way that we jumped from the `main.py` file over to the `crew.py` file, *when* our program gets to *this* point we now need to jump from the `crew.py` over to the code in some file provided to us by `crewai`

BUT this error is telling us that the `crewai` file was nowhere to be found on our machine aka our "mini-machine"

Python has a system called PyPi [https://pypi.org/] that allows us to easily download code published by other members of the Python community

So if we enter this instruction on our mini machine...

- `pip install crewai==0.63.6`

All of the Python code published to PyPi by the CrewAI team will be downloaded onto our "mini-machine"

## Let's run our crew again...

- Let's run our crew again and see what happens

- `python src/our_crew_of_agents/main.py`

- Ok we see something new which is great. That means we fixed the `crewai` import error

## Observe the error

- FileNotFoundError: [Errno 2] No such file or directory: '/code/src/our_crew_of_agents/config/agents.yaml'

Dun, Dun, Dun...