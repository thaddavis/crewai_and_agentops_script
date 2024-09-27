## Try running the crew again

- `python src/crew_of_agents/main.py`
- fix issues

## Add environment variables

- `touch .env`
- `echo "OPENAI_API_KEY=" >> .env`
- replace key
- pip install python-dotenv==1.0.1
- add the following code
```main.py
from dotenv import load_dotenv
load_dotenv()
```