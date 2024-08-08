_Authors_: @manodyaSenevirathne \
_Created_: 2024/08/05 \
_Updated_: 2024/08/05 \
_Edition_: Swan Lake

# Sanitation for OpenAPI specification

This document records the sanitation done on top of the official OpenAPI specification from OpenAI Chat.
The OpenAPI specification is obtained from the [OpenAPI specification for the OpenAI API](https://github.com/openai/openai-openapi/blob/master/openapi.yaml). 
These changes are done in order to improve the overall usability, and as workarounds for some known language limitations.

1. **Removed the `Deprecated: true` property from the below schemas**:

   - **Changed Schemas**: `ChatCompletionRequestAssistantMessage`,`ChatCompletionRequestFunctionMessage`,`ChatCompletionFunctions`,`ChatCompletionResponseMessage`,`ChatCompletionStreamResponseDelta`,`CreateChatCompletionRequest`

   - **Original**:
      - `Deprecated: true`

   - **Updated**:
      - Removed the `deprecated` parameter

   - **Reasons**: The original configuration was generated successfully, but it led to compile-time warnings. To ensure smoother compilation and avoid potential issues, the configuration has been revised.


2. **Removed the `default:null` property of from the below schemas**:

   - **Changed Schemas**: `CreateCompletionRequest`,`ChatCompletionStreamOptions`,`CreateChatCompletionRequest`

   - **Original**:
      - `default: null`

   - **Updated**:
      - Removed the `default` parameter 

   - **Reason**: This change is done as a workaround for ballerina openapi tool not allowing to generate the client.

## OpenAPI cli command

The following command was used to generate the Ballerina client from the OpenAPI specification. The command should be executed from the repository root directory.

```bash
bal openapi -i docs/spec/openapi.yaml --mode client --tags Chat --license docs/license.txt -o ballerina
```
Note: The license year is hardcoded to 2024, change if necessary.