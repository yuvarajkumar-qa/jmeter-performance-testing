# JMeter Performance Testing

Apache JMeter load test plan, non-GUI CLI execution guide, and performance triage notes.

## What's Inside
* **Test Plan (`tests/users_api_load_test.jmx`):** HTTP `GET /users/1` check with status assertion and parameterized `HOST`, `THREADS`, and `LOOPS` properties.
* **Performance Notes (`docs/performance_notes.md`):** Practical notes on p95/p99 latency, non-GUI runs, and bottleneck triage.

## Folder Structure
```text
├── docs/
│   └── performance_notes.md
├── tests/
│   └── users_api_load_test.jmx
└── README.md
