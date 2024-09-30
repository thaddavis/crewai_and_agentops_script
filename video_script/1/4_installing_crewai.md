## Let's now try running our crew

- `python src/our_crew_of_agents/main.py`

Whengh, Whengh, Wheowgh...

I'm intentionally showing these errors so you get a feel for how this stuff really works

## Importing `crewai`

When we ran the `main.py` file, our computer started reading the code (aka the instructions in this file) from top to bottom and when we got to the 1st line we jumped over to the code seen in the `crew.py` file and started reading the instructions over there...

On the 1st line of `crew.py`, you can see we're importing some code being referred to as `crewai`...

But, as the error clearly stated, and as our VSCode editor is indicating, this `crewai` thing is nowhere to be found

So, we need to add it to our dev container so the Python interpreter can find it...

(PAUSE)

Python has a system in its ecosystem called PyPi [https://pypi.org/] (which is short for Python Package Index) that allows us to easily download code published by other members of the Python community.

```.js
function scrollToBottom() {
  const scrollHeight = document.documentElement.scrollHeight;
  const scrollStep = 0.5;  // Number of pixels to scroll each step
  const delay = 20;  // Delay between each scroll step (in milliseconds)

  const scrollInterval = setInterval(() => {
    // Check if the current scroll position is at the bottom
    if (window.scrollY + window.innerHeight < scrollHeight) {
      window.scrollBy(0, scrollStep);  // Scroll down by the defined step
    } else {
      clearInterval(scrollInterval);  // Stop scrolling when the bottom is reached
    }
  }, delay);
}

scrollToBottom();
```

When entering this instruction into our terminal for example...

- `pip install crewai==0.65.2`

code published to PyPi by the CrewAI team will be downloaded onto our dev container in a way that the Python interpreter can access

https://pypi.org/project/crewai/

- Notice how I'm including the specific version of `crewai` so you know exactly what I'm using

- Leaving out the version number and just typing `pip install crewai` will download the latest version of `crewai`

- IF you're following along just download the version I'm using if you're unsure of what to do...

- ENTER THE COMMAND: `pip install crewai==0.65.2`

- It looks like installing `crewai` worked and we see the warning indicators on the import go away in VSCode...

so let's run our project again and see what happens

(PAUSE)

## Let's run our crew again...

- `python src/our_crew_of_agents/main.py`

- We now see something new which is great. That means we fixed the `crewai` import error

## Observe the error

- FileNotFoundError: [Errno 2] No such file or directory: '/code/src/our_crew_of_agents/config/agents.yaml'

- I wonder what this could mean...

Dun, Dun, Dun...

SOUND EFFECT: https://www.youtube.com/watch?v=E6iwa12fGR0