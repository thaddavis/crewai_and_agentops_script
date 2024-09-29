This error is happening because we haven't authenticated our project with OpenAI's platform

CrewAI supports various LLMs for powering the agents in a crew but by default is set up to use OpenAI

If you're unfamiliar with the term LLM...

An LLM is the part of an agent we would most likely call it's brain...

The details of how an LLM works can be explored outside of this video if interested...

But for our purposes, we'll be calling an LLM (powered by OpenAI via their API) each time an agent in our crew needs to perform the current task assigned to it...

Connecting our CrewAI project with OpenAI is simple.

First, we have to sign up on OpenAI's platform: `https://platform.openai.com/`

OpenAI's pricing is usage-based like a gas station so be sure to add a couple dollars of credits to your account

If you've never used OpenAI's platform, I suggest adding the minimum amount allowed as that should be more than enough for what we're doing here

You can always add more credits later if needed

`https://platform.openai.com/api-keys`

And after you have your OpenAI platform account set up, you'll provision and copy an API_KEY

Make sure you keep this key private so no one besides you creates charges on your account

And then here is how we securely add this API key to our project

For the beginners watching this way of adding API key's to a project is actually very common so pay attention closely...

## Add environment variables

- `touch .env`
- `echo "OPENAI_API_KEY=" >> .env`
- pip install python-dotenv==1.0.1
- add the following code
```main.py
from dotenv import load_dotenv
load_dotenv()
```

We have to load in our API KEYS before calling our agents so the API key is ready for them to use...

## If we run the crew again - THIS SHOULD NOW WORK - and indeed it does 🤞

- `python src/our_crew_of_agents/main.py`

√