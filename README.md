# FakeStore API Performance Testing using Apache JMeter

## Project Overview

This project demonstrates performance testing of a real-world e-commerce API (FakeStore API) using Apache JMeter. The goal was to simulate realistic user behavior and evaluate system performance under increasing load conditions.

The performance test simulates a complete shopping flow:

* User Login
* Browse Products
* View Product Details
* Add Product to Cart
* View Cart

This project follows industry-standard performance testing practices including parameterization, correlation, transaction controllers, and load scaling.

---

## Tools Used

* Apache JMeter 5.6.3
* FakeStore API (https://fakestoreapi.com)
* Java 17
* GitHub for version control

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

* Performance Test Design
* Load Testing using Apache JMeter
* Parameterization using CSV Data Set Config
* Correlation using JSON Extractor
* Transaction Controllers usage
* Performance Metrics Analysis
* Test Result Documentation
* GitHub Project Documentation

---

## Author

Bhagyashree Acharya
QA Engineer | Performance Testing Enthusiast
