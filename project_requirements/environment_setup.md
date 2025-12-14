# Environment Setup

For this project you'll use the following libraries:

- chromadb>=1.0.4
- openai>=1.73.0
- pydantic>=2.11.3
- python-dotenv>=1.1.0
- tavily-python>=0.5.4

These are installed in the included workspace.

## Workspace Instructions

Sign up for a free Tavily account, which will allow you to search the web and get back N pages and textual content for the pages, for free (first 1000 requests are free)

After signing up, you can get your API key here: https://app.tavily.com/home(opens in a new tab)(opens in a new tab)

Create a file named .env in the same directory as the project notebook, and a entries for both OPENAI_API_KEY and TAVILY_API_KEY

e.g.

```text
OPENAI_API_KEY="sk-**********"
TAVILY_API_KEY="tvly-********"
```

Use python-dotenv to load the .env file and ensure the appropriate env variables are set:

```python
# Load in the OpenAI key and Tavily key.
# In the project folder, create a file named '.env'
# ensure your .env file contains keys named OPENAI_API_KEY="your key" and TAVILY_API_KEY="your key"
from dotenv import load_dotenv
import os

load_dotenv('config.env')
assert os.getenv('OPENAI_API_KEY') is not None
assert os.getenv('TAVILY_API_KEY') is not None
```
