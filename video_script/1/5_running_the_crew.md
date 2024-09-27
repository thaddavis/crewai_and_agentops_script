## Try running our crew

- `python src/crew_of_agents/main.py`

Whengh, Whengh, Wheowgh...

## Importing `crewai`

We imported `crew.py` from `main.py` and that worked because the `ENV PYTHONPATH=/code` instruction told Python the base point of where to look...

But inside of this file we imported `crewai` from `crew.py`

The same way that we jumped from the main.py file over to the crew.py file, when our program gets to this point we now need to jump from the crew.py over to the code in some file provided to us by `crewai`

BUT `crewai` was nowhere to be found on our machine

So now we have to install it by typing...

- `pip install crewai==0.63.6`