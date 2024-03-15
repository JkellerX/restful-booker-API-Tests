# Restful-booker Application

This repository contains the Restful-booker application, a RESTful API for managing hotel bookings.

## Description

The Restful-booker application occasionally exhibits performance issues, specifically with the `/booking` endpoint when filtering by name. This defect report aims to document the issue, steps to reproduce, expected results, and current findings.

## Defect Report

### Title
Performance Defect for `/booking` - GetBookingIds (Filter by name)

### Description

While analyzing the application for performance, it was noticed that the application sometimes responds slowly to API requests. As a result, 3 tests were conducted at 3 different time intervals for all endpoints to ensure the most reliable results. The results indicated that the restful-booker application indeed exhibits issues for one endpoint, namely retrieving bookings with name filtering. A tolerance threshold of 200 ms was adopted.

### Steps to Reproduce

1. Install the application according to the instructions available at the above address.
2. Install the POSTMAN testing tool.
3. Create an environment for http://localhost:3001/ in POSTMAN.
4. Create a collection for Restful-booker and a request for (GetBookingIds - filter by name).
5. Copy the endpoint from the documentation https://restful-booker.herokuapp.com/booking.
6. Go to the request: GetBookingIds (filter by name).
7. Navigate to the "Tests" tab and select the test script: "Check if response time is less than 200 ms"; save it.
8. Run performance tests: Select the test collection and click the "Run" button in Postman.
9. Set options: see attachment 1.
10. Start the test.
11. Perform 3 tests at 3 different time intervals.

### Expected Result

The application should return requests below 200 ms.

### Current Result

The application returns requests exceeding the parameter above 200 ms every few iterations.

### Summary

The application returns requests exceeding the required range of 200 ms every few iterations. There seems to be no correlation indicating that issues with load/overload occur under specific conditions (e.g., at a certain time of day), as the 3 tests conducted at 3 different time intervals appear similar.

## Contributing

If you'd like to contribute to fixing this performance issue, please fork the repository and submit a pull request.

<img src="images/PerformanceTests.jpg>

<img src="images/PerformanceTests2.jpg>

<img src="images/PerformanceTests3.jpg>

<img src='images/PerformanceTests4.jpg>