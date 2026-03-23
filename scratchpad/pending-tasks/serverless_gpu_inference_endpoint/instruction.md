Modal allows you to deploy scalable, serverless web APIs backed by GPU compute, using class-based lifecycle hooks to optimize resource loading. 

You need to create a serverless HTTP web endpoint that serves a pre-trained generative AI model (e.g., `gpt2`) using a single NVIDIA T4 GPU. The endpoint must accept a POST request containing a JSON payload with a `prompt` key and return the generated text response.

**Constraints:**
- You MUST use a Modal class with the `@modal.enter()` lifecycle decorator to load the model into GPU memory exactly once per container initialization.
- You MUST expose the inference function using the `@modal.web_endpoint(method="POST")` decorator.
- The function MUST NOT re-download or re-load the model weights on every single request.