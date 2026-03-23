When building agentic AI workflows, executing dynamically generated or untrusted code requires heavy isolation to prevent security breaches or system corruption.

You need to implement a secure code execution system that receives an untrusted Python script string (e.g., `print("Hello from the secure sandbox!")`), executes it in complete isolation, and retrieves the output.

**Constraints:**
- You MUST execute the untrusted code using the `modal.Sandbox.create()` API to ensure it runs in an ephemeral, isolated environment.
- You MUST programmatically capture and return the standard output (`stdout`) of the sandboxed process back to the calling function.
- You MUST NOT use Python's built-in `exec()`, `eval()`, or `subprocess` modules directly within the host Modal container to run the untrusted string.