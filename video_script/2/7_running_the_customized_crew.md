## Run the crew again

- Before we run this CrewAI crew of agents and generate a hit song...

- let's review our customizations one last time...

- the agents.yaml looks good

- the tasks.yaml looks good

- the crew.py looks good

- the main.py look good but notice this...

- CrewAI allows us to pass dynamic values to our agents when we run them

- For example instead of hard-coding all the requirements of our song in our config we could've made some aspects dynamic by inserting placeholders...

- For example, let's say we want to customize the genre...

- We could put a placeholder in our config like so { genre } and CrewAI's framework would replace these placeholders with the values provided at kickoff

For example, to easily control the genre that our musicians are specialized in we would do this when calling the crew...

```
inputs = {
  'genre': 'Hip Hop' 
}
FrequencyMusicCrewCrew().crew().kickoff(inputs=inputs)
```

or...

```
inputs = {
  'genre': 'Country' 
}
FrequencyMusicCrewCrew().crew().kickoff(inputs=inputs)
```

or

But let's keep things simple. You can explore the more advanced features offered by CrewAI outside of this video...

```
FrequencyMusicCrew().crew().kickoff()
```

So NOW let's run the crew and see what happens: `crewai run`

## Observe the link to AgentOps

- Alright, looks like we have our hit song

- Let's actually make this song to see what it sounds like