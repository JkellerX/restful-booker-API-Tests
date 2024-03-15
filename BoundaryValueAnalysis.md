# Restful-Booker Application Testing Report

## Introduction
This repository contains a testing report for the Restful-Booker application. The report outlines various tests conducted on the application, including positive and negative scenarios, boundary value analysis, and equivalence class testing.

## Authentication (Login/Logout)
### Status: Minor Issues
#### Defects Found:
- The application sometimes returns status code 201 instead of 200 during ping check.
#### Reproduction Steps:
1. Install the application according to the instructions provided.
2. Install testing tools.
3. Set up the environment for http://localhost:3001/ in POSTMAN.
4. Create a collection and request for Get/Ping - HealthCheck.
5. Copy the endpoint from the documentation: [Ping Documentation](https://restful-booker.herokuapp.com/ping)
#### Expected Result:
The application should return status code 200.
#### Current Result:
The application returns status code 201.
#### Quality Characteristics:
The application provides login and logout functionality but sometimes returns incorrect response codes, affecting system functionality.

## Booking Search (GetBooking)
### Status: Working
#### No Defects Found.
#### Quality Characteristics:
The application provides a booking search function that works correctly and meets user expectations.

## Booking Search by Name (GetBookingIds - Filter by name)
### Status: Not Working
#### Defects Found:
- The application returns an empty response when a valid request is made.
#### Reproduction Steps:
1. Install the application according to the provided instructions.
2. Install testing tools.
3. Set up the environment for http://localhost:3001/ in POSTMAN.
4. Create a collection and request for Getbookingid - filter by name.
5. Copy the endpoint from the documentation: [Booking Search by Name Documentation](https://restful-booker.herokuapp.com/booking?firstname=sally&lastname=brown)
#### Expected Result:
According to the documentation, the application should return an array of objects containing unique booking identifiers.
#### Current Result:
The application returns empty content.
#### Quality Characteristics:
The booking search by name function does not work correctly, impacting system functionality.

...

## Conclusion
Overall, the testing report highlights various defects and issues encountered during testing of the Restful-Booker application. It provides insights into the application's functionality and areas that require improvement.