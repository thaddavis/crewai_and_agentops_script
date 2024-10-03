## CrewAI projects can get quite complicated BUT can can also be very simple

- Let's customize our crew by replacing the default "research" and "analyst" agents with the following agents

```
songwriter:
  role: >
    Songwriter
  goal: >
    Write a Billboard #1 Hit song
  backstory: >
    You're an internationally-acclaimed songwriter with a knack for crafting catchy and commercially successful songs.
    You've written numerous hits for some of the biggest artists in the industry, and you're known for your ability
    to capture the essence of a topic and turn it into a chart-topping hit.

producer:
  role: >
    Music Producer
  goal: >
    Work with the songwriter to produce a #1 Billboard Hit song
  backstory: >
    You're an experienced music producer with a track record of producing hit songs across various genres. Your goal is to 
    output the chord progression, detailed melody, and exact BPM for the song so that your engineer can program the instruments, the artist can perform the melody, 
    and the mixing engineer can then mix the song.
```

If you're wondering how this `agents.yaml` configuration works, the link to the relevant documentation on CrewAI website is linked in the description

In this file we are creating 2 agents, a songwriter and a producer and giving each of them a role, goal, & backstory specified in natural language

https://docs.crewai.com/getting-started/Start-a-New-CrewAI-Project-Template-Method/#agentsyaml

and let's also replace the default tasks provided by the generated project with these ones...

```
songwriting:
  description: >
    Write a song about total accountability
  expected_output: >
    A song with lyrics and detailed melodies.
  agent: songwriter 

producing:
  description: >
    Outline the chord progression and detailed melody for the song written by the songwriter so a performing artist and engineer can record, program, and mix it
  expected_output: >
    Lyrics, detailed melody, and chord progression for the song
  agent: producer
```

and if you're wondering how this `tasks.yaml` configuration works, the link to the relevant documentation on CrewAI website is linked in the description as well

In this file we are creating 2 tasks that will be executed from top to bottom. First we are assiging the task to write a song about accountability to the songwriter and after the song has been been generated it will be passed to a producer who will compose the full song with (chords and melody) in preparation for handoff to an engineer and artist to make it

https://docs.crewai.com/getting-started/Start-a-New-CrewAI-Project-Template-Method/#tasksyaml