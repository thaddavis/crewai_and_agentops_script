This error is because we haven't authenticated our CrewAI project with OpenAI's platform

CrewAI supports various LLMs for powering the agents in a crew but by default is set up to use OpenAI

If you're unfamiliar with the term LLM...

An LLM is the part of an agent responsible for generating output in response to some input

As of the time of recording, most LLM systems are designed to receive and generate text but some are starting to be capable of accepting other forms of data as well...

The details of how an LLM works can be explored outside of this video if interested...

Connecting our CrewAI project with OpenAI is simple.

All we have to do is sign up on OpenAI's platform: `https://platform.openai.com/`

OpenAI pricing model is pay as you use like a gas station. So you might need add a couple dollars of credits to your account.

If you've never used OpenAI's platform, I'd suggest adding the minimum amount allowed to save money

And you can add more credits later as needed

`https://platform.openai.com/api-keys`

After you have your platform account set up...

Provision an API_KEY

And make sure you keep this key private so no one besides you creates charges on your account

And then here is how we securely add this key to our CrewAI project

## Add environment variables

- `touch .env`
- `echo "OPENAI_API_KEY=" >> .env`
- pip install python-dotenv==1.0.1
- add the following code
```main.py
from dotenv import load_dotenv
load_dotenv()
```

As long as we never share the content of this .env file with any other person or system our OpenAI account is protected

## Try running the crew again - THIS SHOULD WORK 🤞

- `python src/our_crew_of_agents/main.py`

√