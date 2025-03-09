_Authors_: @manodyaSenevirathne \
_Created_: 2024/08/05 \
_Updated_: 2024/08/21 \
_Edition_: Swan Lake

# Sanitation for OpenAPI specification

This document records the sanitation done on top of the official OpenAPI specification from OpenAI Chat.
The OpenAPI specification is obtained from the [OpenAPI specification for the OpenAI API](https://github.com/openai/openai-openapi/blob/master/openapi.yaml). 
These changes are done in order to improve the overall usability, and as workarounds for some known language limitations.

1. **Removed the `default:null` property of from the below schemas**:

   - **Changed Schemas**: `CreateCompletionRequest`,`ChatCompletionStreamOptions`,`CreateChatCompletionRequest`

   - **Original**:
      - `default: null`

   - **Updated**:
      - Removed the `default` parameter 

   - **Reason**: This change is done as a temporary workaround until the Ballerina OpenAPI tool supports OpenAPI Specification version v3.1.x (Currently supported upto version 3.0.0).

2. **Added `nullable: true` property to system_fingerprint**:

   - **Changed Schemas**: `CreateCompletionResponse`

   - **Updated**:
      - `system_fingerprint:
         // ... Omitted for brevity 
         nullable = true` 

   - **Reason**: This change explicitly specifies that the system_fingerprint field can be null, which is important for proper schema validation and client code generation.


## OpenAPI cli command

The following command was used to generate the Ballerina client from the OpenAPI specification. The command should be executed from the repository root directory.

```bash
bal openapi -i docs/spec/openapi.yaml --mode client --tags Chat --license docs/license.txt -o ballerina
```
Note: The license year is hardcoded to 2024, change if necessary.
