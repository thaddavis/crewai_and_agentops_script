## Run the crew again

- We are now ready to run a crew and generate our hit song...

- But before we do that let's scan over our work...

- the agent.yaml looks good

- the tasks.yaml looks good

- the crew.py looks good

- the main.py look good but notice this...

- CrewAI allows us to pass dynamic values to our agents when we run them

- For example instead of hard-coding all the requirements of our song in our config we could've made some aspects dynamic by inserting placeholders...

- For example, let's say we wanted to customize the genre...

- We could put a placeholder in our config like so { genre } and CrewAI's framework will replace these placeholders with the values provided at kickoff

For example we could do something like this to easily control the genre that our musicians are specialized in...

```
inputs = {
  'genre': 'Country'
}
FrequencyMusicCrewCrew().crew().kickoff(inputs=inputs)
```

But let's keep things simple for this DEMO. You can explore the advanced features offered by CrewAI, and there are many, outside of this video if interested...

```
FrequencyMusicCrew().crew().kickoff()
```

Let's run the crew again: `crewai run`

## Observe the link to AgentOps

- Ok so now we have our hit song
- Let's actually make this song to see what it sounds like