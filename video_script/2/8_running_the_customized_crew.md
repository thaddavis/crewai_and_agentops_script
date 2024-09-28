## Run the crew again

- Notice how, CrewAI allows us to pass dynamic values to our agents when we run them

- For example instead of hard-coding all the requirements of our song in our config. We could make some aspects of them dynamic by inserting placeholders...

- For example, let's say we wanted to customize the genre...

- We could place a placeholder in our config like so { genre } and CrewAI's framework will replace them with the values provided at kickoff

For example we could do something like this...

```
inputs = {
  'genre': 'Country'
}
FrequencyMusicCrewCrew().crew().kickoff(inputs=inputs)
```

But let's keep it simple for this walkthroug. You can explore more of the advanced features offered by CrewAI if interested outside of this video...

```
FrequencyMusicCrewCrew().crew().kickoff()
```

Let's run the crew again: `crewai run`

## Observe the link to AgentOps

- Ok so now we have our song
- Let's actually make it to see what it sounds like