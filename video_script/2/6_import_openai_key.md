## Let's try running the crew...

- `crewai run`
- OK! there are errors related to a missing OPENAI_API_KEY
  - We see the text "error"
  - error code 401
  - OpenAI Incorrect API key
- So by default CrewAI uses OpenAI as the LLM powering the agents in a crew
- So we need to add an API_KEY for authenticating with OpenAI to our project by including it in the .env