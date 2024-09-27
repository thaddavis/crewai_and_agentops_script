## Run the crew again

- CrewAI allows us to pass in values when we run them for example instead of hard-coding the requirements of our song in our config. We could make some aspects of them dynamic by inserting placeholders

- For example, let's say we wanted to customize the genre...

- We could place { genre } in select places of our crew configuration and replace them at runtime by passing them as input values like so...

```
inputs = {
  'genre': 'Country'
}
FrequencyMusicCrewCrew().crew().kickoff(inputs=inputs)
```

But we are just keeping it simple to get the basics down. And you can explore more of the advanced features offered by CrewAI outside of this video...

```
FrequencyMusicCrewCrew().crew().kickoff()
```

Let's run the crew again: `crewai run`