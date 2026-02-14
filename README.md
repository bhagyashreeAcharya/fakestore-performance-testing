# FakeStore API Performance Testing using Apache JMeter

## Project Overview

This project demonstrates performance testing of a real-world e-commerce API (FakeStore API) using Apache JMeter. The goal was to simulate realistic user behavior and evaluate system performance under increasing load conditions.

The goal was to identify:

• System stability  
• Maximum throughput capacity  
• Response time behavior under load  
• Performance bottlenecks  
• Safe production load limits  

---

## User Flow Simulated

Each virtual user performs the following actions:

1. Login  
2. Browse Products  
3. View Product Details  
4. Add Product to Cart  
5. View Cart  

This project follows industry-standard performance testing practices including parameterization, correlation, transaction controllers, and load scaling.

---

## Tools Used

• Apache JMeter 5.6.3  
• FakeStoreAPI (https://fakestoreapi.com)  
• CSV Data Config (parameterization)  
• JSON Extractor (correlation)  
• Debug Sampler  
• Aggregate Report  
• Summary Report  
• Google Sheets (performance analysis & graphs)

---

## Test Scenario

Simulated user flow:

1. Login using valid user credentials
2. Fetch all products
3. View individual product details
4. Add product to cart
5. View cart using dynamically extracted cartId

---

## Test Data Management

Parameterization implemented using CSV files:

* users.csv → multiple user credentials
* products.csv → multiple product IDs

Correlation implemented using JSON Extractor to dynamically capture cartId.

---

## Load Test Profile

The following load levels were executed:

| Test Type        | Users | Ramp-up (sec) |
| ---------------- | ----- | ------------- |
| Baseline Test    | 1     | 1             |
| Light Load Test  | 10    | 10            |
| Medium Load Test | 50    | 50            |
| Heavy Load Test  | 100   | 100           |
| Stress Test      | 200   | 200           |

---

## Key Performance Metrics Captured

* Average Response Time
* 90th and 95th Percentile Response Time
* Throughput (requests/sec)
* Error Rate (%)

---

## Project Structure

```
test-plan/
    fakestoreapi Shopping Flow.jmx

test-data/
    users.csv
    products.csv

results/
    baseline_1_user.csv
    light_load_10_users.csv
    medium_load_50_users.csv
    heavy_load_100_users.csv
    stress_load_200_users.csv

screenshots/
    test_plan_structure.png
    aggregate_report_10_users.png
    summary_report_10_users.png
    thread_group_100_users.png
    cart_id_extraction.png

Reports/
    performance_analysis.md

```

---

## Correlation Implementation

Dynamic cartId extraction was implemented using JSON Extractor.

Example:

```
POST /carts → extract cartId
GET /carts/${cartId} → verify cart
```

This ensures realistic simulation of dynamic user sessions.

---

## Test Execution Evidence

All test results are available in the results folder as CSV files exported directly from JMeter Aggregate Report.

Screenshots are provided as visual proof of test execution.

---

## Key Skills Demonstrated

* Apache JMeter  
* Performance Test Design
* API Testing
* Test Plan Desing
* Load Testing using Apache JMeter
* Parameterization using CSV Data Set Config
* Correlation using JSON Extractor
* Transaction Controllers usage
* Performance Metrics Analysis (P95, P99)
* Percentile Analysis (P95, P99)
* Throughput Analysis  
* Bottleneck Identification
* Capacity Planning   
* Test Result Documentation
* GitHub Project Documentation


---

## Author

Bhagyashree Acharya
QA Engineer | Performance Testing Enthusiast
