This error is happening because we haven't authenticated our CrewAI project with OpenAI's platform

CrewAI supports various LLMs for powering the agents in a crew but by default is set up to use OpenAI

If you're unfamiliar with the term LLM...

An LLM is the part of an agent we would most likely call it's brain...

At the time of recording, most LLM systems are designed to receive and generate text but some are starting to be capable of accepting other forms of data as well...

The details of how an LLM works can be explored outside of this video if your interested...

For our purposes, we will be calling an LLM powered by OpenAI via their API each time an agent in our crew need to perform a task assigned to it...

Connecting our CrewAI project with OpenAI is simple.

First, we have to sign up on OpenAI's platform: `https://platform.openai.com/`

OpenAI's pricing is usage-based like a gas station. So you might need to add a couple dollars of credits to your account.

If you've never used OpenAI's platform, I'd suggest adding the minimum amount allowed as that should be more than enough for what we're doing here

You can always add more credits later if needed

`https://platform.openai.com/api-keys`

After you have your OpenAI platform account set up...

You'll provision an API_KEY

Make sure you keep this key private so no one besides you creates charges on your account

And then here is how we securely add this API key to our CrewAI project

## Add environment variables

- `touch .env`
- `echo "OPENAI_API_KEY=" >> .env`
- pip install python-dotenv==1.0.1
- add the following code
```main.py
from dotenv import load_dotenv
load_dotenv()
```

In `main.py`, we have to load in our API_KEY BEFORE calling our agents so the API key is ready for them to use...

As long as we never share the content of this .env file with any other person or system, our OpenAI account is protected from abuse by others

## If we run the crew again - THIS SHOULD WORK - and indeed it does 🤞

- `python src/our_crew_of_agents/main.py`

√