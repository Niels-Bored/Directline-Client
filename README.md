
## DirectLine Client

Direct Line is the REST API used to communicate directly with Copilot Studio bots from external applications, so this library is intended to facilitate its use in Python.

### Installation
You can install this library through pip.
```bash

pip install directline-client

```
### Quickstart

```python
from directline_client import DirectLineClient

client = DirectLineClient(secret="YOUR_SECRET_KEY")
print(client.call_llm("Hello!"))
```
### Features

-   Start new conversations
    
-   Maintain conversation context automatically
    
-   Simple text generation through `.call_llm()` method
    

### Import DirectLineClient class

First, you'll need to import the DirectLineClient class to instantiate an object.

```python

from  directline_client  import  DirectLineClient

```

  

### How to use DirectLineClient class

To use a Copilot Studio model through Direct Line Client, it's necessary to get your secret key.

#### Params 

- secret (str, optional): The Direct Line secret (required to authenticate).
- endpoint (str, optional): Base Direct Line API endpoint.
Default: "https://directline.botframework.com/v3/directline"
- user_name (str, optional): Display name for the user sending messages. 
Default: "PythonUser"

####  Attributes
- secret (str): Authentication secret.
- endpoint (str): Target Direct Line endpoint.
- user_id (str): Randomly generated unique identifier for the client.
- conversation_id  (str | None): ID of the active conversation.
- watermark (str): Tracks last processed bot message.
- headers (dict): Authorization header for Direct Line.
- user_name (str): User display name.

#### How to get your Copilot Studio Secret Key

- The first step is to access the Copilot Studio platform and select the agent you want to use.

- Then in the security section, select Authentication and copy one of your secret keys.

- Finally, publish the agent.

#### Instantiate the object

Once you have your secret key, you'll be able to instantiate a DirectLineClient object.

  

```python

client  =  DirectLineClient(secret=YOUR_SECRET_KEY)

```

### Usage Example

To use your Copilot Studio agent and generate text from a prompt, call it like this:

  

```python

response  =  client.call_llm("Hello bot!")

```

`call_llm()` returns a simple string with the model response.

  

### Follow Up Conversations

  

DirectLineClient automatically creates a conversation_id that allows you to continue a specific conversation, but you can start a new one anytime. To start a new conversation flow you just call `start_conversation()`.

`start_conversation()` resets the current conversation by requesting a new `conversationId` from the Direct Line API. The next `call_llm()` call will begin a fresh thread.

```python
response  =  client.call_llm("How many states are there in the USA?")

  

print(response)

# The United States has 50 states.  

response  =  client.call_llm("Now, how many of them begin with the letter A?")

print(response)

# Four U.S. states begin with the letter A: Alabama, Alaska, Arizona, and Arkansas.  

client.start_conversation()

response  =  client.call_llm("Now, how many of them begin with the letter A?")

print(response)

# There are five elements that begin with the letter A: Actinium, Aluminum, Americium, Antimony, and Argon. If you need information about any of them, let me know.
```

**Note:** The client preserves context **as long as the conversationId remains active**.