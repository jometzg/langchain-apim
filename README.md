# Langchain with APIM
This repo is a demonstration of how OpenAI behind APIM using langchain as the orchestrator should require no code changes beyond that of the endpoints and connection settings.

Use the included Jupyter notebook to run the samples. You will need your own endpoints and connection strings.

Note that this version does not use OAuth tokens, but may be adapted to use these:

for a service principal:
```
token = get_access_token("https://login.microsoftonline.com/YOUR_TENANT/oauth2/v2.0/token", client_id,client_secret,"api://YOUR_CLIENT_ID/.default")
```

Or better using DefaultAzureCredential. See [here](https://python.langchain.com/docs/integrations/llms/azure_openai/)

```
import os
from azure.identity import DefaultAzureCredential

# Get the Azure Credential
credential = DefaultAzureCredential()

# Set the API type to `azure_ad`
os.environ["OPENAI_API_TYPE"] = "azure_ad"
# Set the API_KEY to the token from the Azure credential
os.environ["OPENAI_API_KEY"] = credential.get_token("https://cognitiveservices.azure.com/.default").token
```
