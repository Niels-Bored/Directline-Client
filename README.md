## DirectLine Client
A Python library intended to facilitate the use of Copilot Studio agents through code.

### Import DirectLineClient class
First, you'll need to import the DirectLineClient class to instantiate an object.
```bash
from directline_client import DirectLineClient
```

###  How to use DirectLineClient class
In order to use a Copilot Studio model through Direct Line client, it's necessary to get your secret key.
#### How to get your Copilot Studio Secret Key
- The first step is to access the Copilot Studio platform and select the agent you want to use. 
- Then in the security section, select Authentication and copy one of your secret keys. 
- Finally, publish the agent. 
####  Instantiate the object
Once you have your secret key, you'll be able to instantiate a DirectLineClient object.

```bash
client = DirectLineClient(secret=YOUR_SECRET_KEY)
```
###  Call the LLM
To use your Copilot Studio agent and generate text from a prompt, call it like this:

```bash
response = client.call_llm("Hello bot!")
```
This function returns a simple string with the model response.