# Chating with OpenAI using Python

This guide will walk you through the process of building your very own custom ChatGPT, leveraging the flexibility and simplicity of Python programming.

Prerequisite: Knowledge of Python and a paid OpenAI account ( I thought there would be some free credits, but there weren’t. So, I bought $5 worth to test it out)

[Billing Overview](https://platform.openai.com/settings/organization/billing/overview)

[Create an OpenAI key using the Create New Secret Key Option.](https://platform.openai.com/settings/profile?tab=api-keys)

## Cost and Tokens?

```json
Cost is calculated based on openAI model and input/output tokens in millions.

e.g.
Model              Input               Output
----------------------------------------------------------
gpt-4o             $5.00  / 1M tokens  $15.00 / 1M tokens
gpt-4-turbo        $10.00 / 1M tokens  $30.00 / 1M tokens
gpt-3.5-turbo-0125 $0.50  / 1M tokens  $1.50  / 1M tokens

What are tokens?

Tokens can be thought of as pieces of words.Before the API processes
the request, the input is broken down into tokens.Here are some helpful
rules of thumb for understanding tokens in terms of lengths:

1 token ~= 4 chars in English
1 token ~= ¾ words
100 tokens ~= 75 words

Or

1-2 sentence ~= 30 tokens
1 paragraph ~= 100 tokens
1,500 words ~= 2048 tokens

```

[OpenAI Pricing information](https://openai.com/api/pricing/)

[What are tokens and how do you count them?](https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them)

## The Code

I tried the async approach and encapsulated the logic into an AsyncOpenAIBot class. To use the AsyncOpenAIBotclass, you must provide a valid OpenAI API key when creating an instance of the class. This key is used to authenticate your requests to the OpenAI API.

```python
import openai
from openai import AsyncOpenAI
from typing import Callable, Any
class AsyncOpenAIBot:

    def __init__(self, api_key):
        self.client = AsyncOpenAI(api_key = api_key)

    async def get_response(self, prompt:str, callback: Callable[[Any], None], model: str = "gpt-3.5-turbo"):
        try:
            response = await  self.client.chat.completions.create(
                model=model,
                messages=[{"role": "user","content": prompt}]
            )
            callback(response.choices[0].message.content.strip())

        except openai.RateLimitError as e:
            raise Exception(f"Rate limit exceeded. Please try again later. {e}");
        except openai.AuthenticationError as e :
            raise Exception(f"Authentication failed. Please check your API key. {e}");
        except openai.OpenAIError as e:
            raise Exception(f"An error occurred:. {e}");
```

```python
def my_callback(response):
    print("Received response:", response)

def run_bot_async():
    import asyncio
    openai_key = os.getenv("OPENAI_API_KEY")
    if openai_key is None:
        print("Please set OPENAI_API_KEY environment variable")
        exit(1)

   openai_bot = AsyncOpenAIBot(openai_key)
    while True:
        user_input = input("Enter your question:").lower()
        if user_input == "exit":
            break
        asyncio.run(openai_bot.get_response(user_input, my_callback))


if __name__ == "__main__":
    try:
        run_bot_async()
    except Exception as e:
        print(e)
```

Other Useful Links
[OpenAI Usage Stats](https://platform.openai.com/usage)

[OpenAI Python SDK](https://github.com/openai/openai-python)

## Library and Code

I have encapsulated this functionality into my Python library . It has both synchronous and async ways to connect to OpenAI.

```python
pip install omnijp
```

[Go through the readme for more details](https://pypi.org/project/omnijp/2.7.0/)

[Also, feel free to look at the code in Git](https://github.com/jpothanc/omnijp)
