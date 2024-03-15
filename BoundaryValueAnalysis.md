<p align="left">
    <img src="https://skillicons.dev/icons?i=github,postman,github,postman,github,postman,github,postman,github,postman,github,postman,github,postman,github" />
</p>

# Restful-Booker Application Testing Report

## Introduction
This repository contains a testing report for the Restful-Booker application. The report outlines various tests conducted on the application, including positive and negative scenarios, boundary value analysis, and equivalence class testing.

# Equivalence Partitioning and Boundary Value Analysis Tests

## Equivalence Partitioning:

1) Positive Test for Creating an Authentication Token:

**Description:**
- Test data from the API documentation was used, providing a correct username and password (see Attachment 1).
- Expected result: successful creation of an authentication token.
- Actual result: as expected.

<div style="display: flex; justify-content: center;">
    <img src="https://github.com/JkellerX/restful-booker-API-Tests/blob/master/images/equivalenceClass1.jpg" alt="PerformanceTests" style="width: 100%; max-width: 600px;">
</div>

2) Negative Test for Creating an Authentication Token:

**Description:**
- Incorrect behavior of the application - returned status code 200 and response: "reason" bad credentials.
- Reproduction steps:
  - Provided incorrect data: wrong username and password (see Attachment 2).
  - Expected result: response contains an appropriate error message - 401 Unauthorized and response: "reason" bad credentials.
  - Actual result: the application returned status code 200 and response: "reason" bad credentials.

  <div style="display: flex; justify-content: center;">
    <img src="" alt="https://github.com/JkellerX/restful-booker-API-Tests/blob/master/images/equivalenceClass2.jpg" style="width: 100%; max-width: 600px;">
</div>

## Boundary Value Analysis:

### Boundary Value Test for Date When Creating a New Reservation:

**Description:**
- Use a boundary date, e.g., the earliest possible date (year, month, day).
- Check if the application handles this date correctly when creating a reservation.

### Maximum Value for Total Reservation Price:

**Description:**
- Check if the application correctly handles the maximum possible value for the total reservation price.
- Reproduction steps:
  - Execute a PUT request to the /booking/:id endpoint with the reservation identifier and data, where the totalprice value is set to the maximum possible value, in this case, it is the value: 1000000000000000000000.
  - Check the server response.
  - Expected result: The application correctly updates the reservation with the maximum possible value of the total price. The server returns response code 200 OK and returns the updated reservation details, where the totalprice value equals the maximum possible value.
  - Actual result: Error - the application limits the totalprice value to the unit level, even when the maximum value is provided. A response was received where totalprice equals 1.

  <div style="display: flex; justify-content: center;">
    <img src="" alt="https://github.com/JkellerX/restful-booker-API-Tests/blob/master/images/boundaryValue.jpg" style="width: 100%; max-width: 600px;">
</div>

**Limitations of Techniques:**
- Equivalence Partitioning: Does not consider extreme cases, which may lead to missing some test scenarios.
- Boundary Value Analysis: Focuses mainly on extreme cases, often overlooking other important test cases. It may be time-consuming due to the need to analyze many boundary values.



