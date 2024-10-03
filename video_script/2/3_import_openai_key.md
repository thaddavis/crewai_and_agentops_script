## Integrate with OpenAI

Connecting a CrewAI project with OpenAI is simple.

First we have to sign up on OpenAI's platform: `https://platform.openai.com/`

OpenAI's pricing is usage-based just like a gas station. So you might need to add a couple dollars of credits to your account.

I suggest adding whatever the minimum allowed amount is

`https://platform.openai.com/api-keys`

After you have your platform account set up...

Provision an API_KEY

And make sure you keep this key private so no one besides you can create charges on your account

Copy the API KEY and here is how we securely add it to our CrewAI project

## Add environment variables

- `touch .env`
- `echo "OPENAI_API_KEY=" >> .env`
- pip install python-dotenv==1.0.1
- add then add the following code to the main.py file
```main.py
from dotenv import load_dotenv
load_dotenv()
```

As long as we never share the content of this .env file with any other person or system, our OpenAI account is protected

## Run the crew

- After setting up the OPENAI_API_KEY, let's try running the crew again...
- `crewai run`

## Progress

- Should be looking good

## JUST IN CASE the console output is showing warnings

```
import warnings
warnings.filterwarnings("ignore", message="invalid escape sequence")
```