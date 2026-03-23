Event-driven architectures often rely on decoupled message passing and distributed state tracking to manage background processing jobs.

You need to create an asynchronous task system utilizing Modal's distributed primitives. Implement a Producer function that pushes 10 unique job IDs to a distributed queue. Implement a background Consumer function that continuously polls the queue, simulates a processing task for each ID, and updates the final processing status of each job in a shared dictionary.

**Constraints:**
- You MUST use a `modal.Queue` to pass the job IDs from the Producer to the Consumer.
- You MUST use a `modal.Dict` to track the status of the completed jobs (e.g., `{job_id: "COMPLETED"}`).
- The main local entrypoint MUST wait and verify that the `modal.Dict` successfully contains all 10 completed jobs before exiting.