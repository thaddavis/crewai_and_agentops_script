## CrewAI projects can get quite complicated BUT can can also be very simple

- So let's customize our crew by replacing the default "research" and "analyst" agents with the following agents

https://docs.crewai.com/getting-started/Start-a-New-CrewAI-Project-Template-Method/#agentsyaml

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

and let's also replace the default tasks provided by the generated project with these ones...

https://docs.crewai.com/getting-started/Start-a-New-CrewAI-Project-Template-Method/#tasksyaml

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