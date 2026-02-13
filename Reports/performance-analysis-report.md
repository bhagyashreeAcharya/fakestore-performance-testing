
# FakeStore API Performance Analysis Report

## Objective
Evaluate performance, scalability, and stability of FakeStore API under simulated load using Apache JMeter.

User Flow Tested:
Login → Browse Products → View Product → Add Cart → View Cart

---

## Test Environment

Tool: Apache JMeter 5.6.3  
Protocol: HTTPS  
API: fakestoreapi.com  
Test Machine: Windows  
Test Type: Load Testing  

---

## Load Levels Tested

| Load Level | Users |
|-----------|------|
| Baseline | 1 |
| Light | 10 |
| Medium | 50 |
| Heavy | 100 |
| Stress | 200 |

---

## Performance Summary

| Users | Avg Response Time (ms) | Throughput (req/sec) | Error Rate |
|------|------------------------|----------------------|-----------|
| 1 | 366 | 2.72 | 0% |
| 10 | 274 | 5.59 | 0% |
| 50 | 277 | 5.92 | 0% |
| 100 | 252 | 5.98 | 0% |
| 200 | 293 | 5.99 | 0% |

---

## Response Time Analysis

Graph: response_time_vs_users.png

Observation:
- Response time improved as load increased to 100 users
- Indicates efficient backend handling
- Slight increase at 200 users indicates approaching capacity
- System remains stable

---

## Throughput Analysis

Graph: throughput_vs_users.png

Observation:
- Throughput increases with load
- Stabilizes near 6 req/sec
- Indicates backend saturation point

---

## Error Analysis

Error rate observed: 0%

System handled all requests successfully.

---

## Scalability Conclusion

System shows:

- Good scalability
- Stable performance
- No failures
- Proper handling of concurrent users

Performance is stable up to 200 users.

---

## Correlation Implementation

Cart ID extracted dynamically using JSON Extractor:

Variable: cartId  
JSON Path: $.id  

Used in request:

/carts/${cartId}

---

## Final Conclusion

FakeStore API demonstrated stable and reliable performance under load.

System is capable of handling concurrent users without failures.

