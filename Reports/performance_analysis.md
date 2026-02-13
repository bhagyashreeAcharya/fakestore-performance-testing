# Performance Test Analysis – FakeStore API

## Test Objective

Evaluate system performance under increasing user load and identify response time trends, throughput behavior, and system stability.

---

## Load Levels Tested

| Load Level  | Users | Ramp-up |
| ----------- | ----- | ------- |
| Baseline    | 1     | 1 sec   |
| Light Load  | 10    | 10 sec  |
| Medium Load | 50    | 50 sec  |
| Heavy Load  | 100   | 100 sec |
| Stress Load | 200   | 200 sec |

---

## Response Time Analysis

Observation:

* Response time increased gradually as user load increased.
* No sudden spikes or abnormal delays observed.
* System handled concurrent users efficiently under tested load levels.

Expected behavior confirmed:
Higher load results in increased response time due to server resource utilization.

---

## Throughput Analysis

Observation:

* Throughput increased proportionally with user load.
* Indicates system is capable of handling concurrent requests efficiently.

This shows proper scalability behavior.

---

## Error Rate Analysis

Observation:

* Error rate remained at 0% during all load levels.
* Indicates system stability under simulated load conditions.

---

## Correlation Verification

Dynamic cartId extraction using JSON Extractor worked successfully.

Verified using Debug Sampler.

This confirms realistic user session simulation.

---

## Performance Conclusion

System performed reliably under load up to 200 concurrent users.

No critical performance bottlenecks observed.

Response time increase was gradual and within acceptable limits.

System demonstrated stable and scalable behavior under tested load conditions.

---

## Overall Result

Performance Test Status: PASS

System is capable of handling expected user load efficiently.
