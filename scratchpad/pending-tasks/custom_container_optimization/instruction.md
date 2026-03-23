To achieve sub-second cold starts for heavy AI models, dependencies and model weights should be cached directly inside the container image during the build phase.

You need to define a custom `modal.Image` that downloads and caches the weights for a specific HuggingFace transformer model (e.g., `bert-base-uncased`) directly into the container filesystem at build time. Write a Modal runtime function that uses this image to load the model and generate a dummy inference result.

**Constraints:**
- You MUST download the model weights during the image build process using `image.run_function()` or `image.run_commands()`.
- You MUST set the environment variable `HF_HUB_OFFLINE=1` (or equivalent) for the runtime function to definitively prove that no network requests are made to HuggingFace during the container cold start.
- The runtime function MUST load the weights exclusively from the local cached directory established during the build.