# FakeStore API Performance Analysis Report

---

# 1. Executive Summary

Performance testing was conducted on FakeStore API using Apache JMeter to evaluate system performance, scalability, and stability under increasing concurrent user load.

A realistic e-commerce user flow was simulated:

Login → Browse Products → View Product → Add Cart → View Cart

The system demonstrated stable performance, zero failures, and reached maximum throughput capacity at approximately 100 concurrent users.

Beyond this point, throughput plateaued and high-percentile response times increased, indicating system saturation.

---

# 2. Test Objective

Primary objectives:

• Measure system response time under load  
• Identify maximum throughput capacity  
• Analyze percentile response time (P95, P99)  
• Detect performance bottlenecks  
• Determine safe operating capacity  

---

# 3. Test Environment

| Component | Value |
|---------|------|
| Tool | Apache JMeter 5.6.3 |
| Protocol | HTTPS |
| API Tested | fakestoreapi.com |
| Test Machine | Windows |
| Test Type | Load Testing |
| Correlation | JSON Extractor |
| Parameterization | CSV Data Set Config |

---

# 4. User Flow Simulated

Each virtual user performed the following actions:

1. Login  
2. Browse Products  
3. View Product Details  
4. Add Product to Cart  
5. View Cart  

Correlation implemented:

POST /carts → Extract cartId  
GET /carts/${cartId} → View Cart  

This ensures realistic session simulation.

---

# 5. Load Profile Executed

| Load Level | Concurrent Users | Ramp-up Time |
|-----------|-----------------|-------------|
| Baseline | 1 | 1 sec |
| Light Load | 10 | 10 sec |
| Medium Load | 50 | 50 sec |
| Heavy Load | 100 | 100 sec |
| Stress Load | 200 | 200 sec |

---

# 6. Performance Metrics Summary

| Users | Avg Response (ms) | P95 (ms) | P99 (ms) | Throughput (req/sec) | Error Rate |
|------|------------------|----------|----------|----------------------|-----------|
| 1 | 366 | 978 | 978 | 2.72 | 0% |
| 10 | 274 | 436 | 702 | 5.59 | 0% |
| 50 | 277 | 420 | 625 | 5.92 | 0% |
| 100 | 252 | 407 | 529 | 5.98 | 0% |
| 200 | 293 | 496 | 909 | 5.99 | 0% |

---

# 7. Response Time Analysis

## Response Time vs Concurrent Users

![Response Time vs Users](../screenshots/response_time_vs_users.png)

Observation:

• Average response time remained stable between 250–300 ms  
• Performance improved initially due to efficient resource utilization  
• Slight increase at 200 users indicates system approaching capacity  

Conclusion:

System maintains stable average performance under load.

---

# 8. P95 Response Time Analysis

## P95 Response Time vs Concurrent Users

![P95 Response Time vs Users](../screenshots/P95 Response Time vs Concurrent Users.png)


P95 represents worst response time experienced by 95% of users.

Observation:

• P95 improved significantly after baseline  
• Stabilized between 400–500 ms  
• Slight increase at 200 users  

Conclusion:

System handles most user requests efficiently.

---

# 9. P99 Response Time Analysis (Critical Metric)

## P99 Response Time vs Concurrent Users

![P99 Response Time vs Users](../screenshots/P99 Response Time vs Concurrent Users.png)


P99 represents worst response time experienced by 99% of users.

This is the most important real-world performance indicator.

Observation:

• P99 response time increased significantly at 200 users
• Reached 909 ms at stress load

Interpretation:

System is reaching performance limits.

Some requests are delayed due to resource contention.

This is early evidence of system saturation.

---

# 10. Throughput Analysis

## Throughput vs Concurrent Users

![Throughput vs Users](../screenshots/Throughput vs Concurrent Users.png)


Observation:

• Throughput increased rapidly from 1 to 50 users  
• Throughput plateaued at approximately 6 requests/sec  
• No throughput increase beyond 100 users  

Conclusion:

System reached maximum processing capacity at 100 users.

Adding more users did not increase system output.

This confirms backend saturation point.

---

# 11. Error Rate Analysis

Error Rate: 0%

Observation:

• No request failures observed  
• System remained stable even at stress load  

Conclusion:

System demonstrates strong reliability and stability.

---

# 12. Bottleneck Identification

Bottleneck indicators observed at 200 users:

• Throughput stopped increasing  
• P99 response time increased sharply  
• Response time degradation began  

Conclusion:

Backend reached maximum processing capacity.

Requests began queueing under heavy load.

---

# 13. System Capacity Conclusion

Maximum throughput capacity:

≈ 6 requests/sec

Safe operating load:

Up to 100 concurrent users

Beyond this point:

• No throughput improvement  
• Increased response latency  
• Reduced performance efficiency  

---

# 14. Scalability Analysis

System demonstrated:

• Good horizontal scalability up to 100 users  
• Stable response times  
• No system failures  

Scalability limitation begins beyond 100 concurrent users.

---

# 15. Stability Analysis

System remained fully stable during testing.

No crashes  
No errors  
No failed transactions  

This confirms system robustness.

---

# 16. Correlation Implementation

Dynamic cartId extraction implemented using JSON Extractor.

Example:

Extract:

$.id → cartId

Used in:

GET /carts/${cartId}

This ensures accurate session simulation.

---

# 17. Final Conclusion

FakeStore API demonstrates strong performance characteristics under load.

Key findings:

• Stable performance up to 100 concurrent users  
• Maximum throughput capacity ≈ 6 requests/sec  
• No errors observed  
• Backend saturation begins beyond 100 users  
• P99 latency increase indicates performance limits  

System is suitable for moderate concurrent load scenarios.

---

# 18. Recommendations

Recommended production load:

≤ 100 concurrent users

Recommended improvements for higher scalability:

• Load balancing  
• Horizontal scaling  
• Infrastructure optimization  
• Performance monitoring  

---

# End of Report
