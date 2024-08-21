## Overview

[OpenAI](https://openai.com/), an AI research organization focused on creating friendly AI for humanity, offers the [OpenAI API](https://platform.openai.com/docs/api-reference/introduction) to access its powerful AI models for tasks like natural language processing and image generation.

The `ballarinax/openai.chat` package offers functionality to connect and interact with [chat completion related endpoints of OpenAI REST API v1](https://platform.openai.com/docs/api-reference/chat) Enabling seamless interaction with the advanced GPT-4 models developed by OpenAI for diverse conversational and text generation tasks.

## Setup guide

To use the OpenAI Connector, you must have access to the OpenAI API through a [OpenAI Platform account](https://platform.openai.com) and a project under it. If you do not have a OpenAI Platform account, you can sign up for one [here](https://platform.openai.com/signup).

#### Create a OpenAI API Key

1. Open the [OpenAI Platform Dashboard](https://platform.openai.com).

2. Navigate to Dashboard -> API keys.
<img src=https://raw.githubusercontent.com/ballerina-platform/module-ballerinax-openai.chat/main/docs/setup/resources/navigate-api-key-dashboard.png alt="OpenAI Platform" style="width: 70%;">

3. Click on the "Create new secret key" button.
<img src=https://raw.githubusercontent.com/ballerina-platform/module-ballerinax-openai.chat/main/docs/setup/resources/api-key-dashboard.png alt="OpenAI Platform" style="width: 70%;">

4. Fill the details and click on Create secret key.
<img src=https://raw.githubusercontent.com/ballerina-platform/module-ballerinax-openai.chat/main/docs/setup/resources/create-new-secret-key.png alt="OpenAI Platform" style="width: 70%;">

5. Store the API key securely to use in your application.
<img src=https://raw.githubusercontent.com/ballerina-platform/module-ballerinax-openai.chat/main/docs/setup/resources/saved-key.png alt="OpenAI Platform" style="width: 70%;">

## Quickstart

To use the `OpenAI Chat` connector in your Ballerina application, update the `.bal` file as follows:

### Step 1: Import the module

Import the `ballerinax/openai.chat` module.

```ballerina
import ballerinax/openai.chat;
```

### Step 2: Create a new connector instance

Create a `chat:Client` with the obtained API Key and initialize the connector.

```ballerina
configurable string token = ?;

final chat:Client openAIChat = check new({
    auth: {
        token
    }
});
```

### Step 3: Invoke the connector operation

Now, you can utilize available connector operations.

#### Generate a response for given message

```ballerina
public function main() returns error? {

    // Create a chat completion request.
    chat:CreateChatCompletionRequest request = {
        model: "gpt-4o-mini",
        messages: [{
            "role": "user",
            "content": "What is Ballerina programming language?"
            }]
    };

    chat:CreateChatCompletionResponse response = check openAIChat->/chat/completions.post(request);
}
```

### Step 4: Run the Ballerina application

```bash
bal run
```

## Examples

The `OpenAI Chat` connector provides practical examples illustrating usage in various scenarios. Explore these [examples](https://github.com/module-ballerinax-openai.chat/tree/main/examples/), covering the following use cases:

1. [CLI assistant](https://github.com/ballerina-platform/module-ballerinax-openai.chat/tree/main/examples/cli-assistant) - Execute the user's task description by generating and running the appropriate command in the command line interface of their selected operating system.
2. [Image to markdown document converter](https://github.com/ballerina-platform/module-ballerinax-openai.chat/tree/main/examples/image-to-markdown-converter) - Generate detailed markdown documentation based on the image content.