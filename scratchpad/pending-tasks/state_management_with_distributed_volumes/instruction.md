Complex data pipelines require persistent state and shared storage to pass heavy artifacts between decoupled functions without memory overhead.

You need to build a two-step data pipeline using a shared `modal.Volume`. The first Modal function (the "Scraper") must generate a dummy dataset of 5 distinct CSV files and save them directly to a mounted volume path. The second Modal function (the "Analyzer") must read these 5 CSV files from the exact same volume, concatenate their contents, and return a final row count to the local environment.

**Constraints:**
- Both functions MUST mount the same `modal.Volume` instance (e.g., to `/data`).
- Data MUST be written to and read from the shared volume file path; you cannot pass the dataset directly in memory or via function return values between the Scraper and Analyzer.
- The pipeline MUST complete sequentially, ensuring the Scraper finishes writing before the Analyzer begins reading.