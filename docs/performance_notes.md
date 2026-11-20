# Performance Testing Notes & Bottleneck Analysis

## Baseline Approach
* **Non-GUI CLI execution:** Always run load tests in non-GUI mode (`jmeter -n -t ...`) so JMeter itself does not consume extra memory or skew response times.
* **Parameterization:** Pass `THREADS`, `LOOPS`, and `HOST` via `-J` properties so smoke load runs stay fast while stress or soak runs can scale without editing the `.jmx` file.

## Key Metrics Watched
* **p95 & p99 latency:** Averages hide slow outliers—p95/p99 shows what frustrating users actually experience.
* **Error rate & timeouts:** Any `5xx` responses or connection timeouts under ramp-up point to pool exhaustion, slow queries, or upstream throttling.
* **Throughput vs. concurrency:** Look for the point where adding virtual users increases latency and errors instead of increasing completed requests per second.

## Sample Bottleneck Triage Checklist
1. Separate **client/network jitter** (e.g., public test API latency or machine CPU) from **application/DB slowness**.
2. Check slow SQL queries, missing indexes, or lock contention on read/write endpoints under concurrent load.
3. Re-test with identical ramp-up and log outputs before and after any fix to verify real improvement.
