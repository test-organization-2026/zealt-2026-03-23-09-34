Modal's execution model allows replacing sequential processing loops with highly distributed parallel maps, instantly scaling out to hundreds of container workers.

You need to write a script that processes a mock dataset of 100 audio file identifiers (e.g., strings representing file URLs or IDs). You must create a Modal function that simulates a transcription task (e.g., sleeping for 1 second, then returning an uppercase version of the string) and execute it across multiple concurrent workers.

**Constraints:**
- You MUST execute the tasks in parallel using the `.map()` or `.starmap()` method on the Modal function.
- The parent script MUST successfully collect and aggregate all 100 processed strings into a single list and print the results locally.
- You MUST configure the task to allow at least 10 concurrent containers to process the batch simultaneously.