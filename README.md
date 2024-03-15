<p align="center">
    <img src="https://skillicons.dev/icons?i=github,postman,github,postman,github,postman,github,postman,github,postman,github,postman,github,postman,github" />
</p>
# Restful-booker-API-Tests

Restful-booker is a web API interface that allows for creating, reading, updating, deleting, equipped with authentication features and containing plenty of bugs for testing. The API comes pre-loaded with 10 records that you can work with, and it resets to its default state every 10 minutes. Restful-booker also includes detailed API documentation that will help you start testing the API right away. 
t is an open-source application that performs basic CRUD (Create, Read, Update, Delete) operations, which are actions of creating, reading, updating, and deleting data used in applications. Choosing such a system allows for demonstrating a range of different functionalities.

Sources:

-https://automationintesting.online - Preview site
-https://restful-booker.herokuapp.com/apidoc/index.html - Documentation
-https://github.com/mwinteringham/restful-booker - Public and free repository with installation instructions.

<p align="center">
    <img src="https://skillicons.dev/icons?i=github,postman,github,postman,github,postman,github,postman,github,postman,github,postman,github,postman,github" />
</p>

# API Tests Report

Here is a list of the main functionalities of the Restful-Booker application:

1. **Authentication (Login/Logout):** Users can log in to the system by providing correct authentication data, and log out to end the session.

2. **Booking Search (GetBooking):** Allows users to retrieve detailed information about existing bookings.

3. **Booking Search by Name (GetBookingIds - Filter by name):** Enables searching for bookings based on the user's name or other criteria.

4. **Booking Search by Date (GetBookingIds - Filter by date):** Allows filtering bookings based on the check-in and check-out dates.

5. **Creating a New Booking (CreateBooking):** Users can make a new booking by providing required data such as first name, last name, check-in and check-out dates, and other details.

6. **Updating an Existing Booking (UpdateBooking):** Allows users to update existing bookings, such as changing the check-in or check-out dates.

7. **Deleting a Booking (DeleteBooking):** Enables users to delete existing bookings from the system.

## Conducted Tests and Found Defects

# Application Testing Report

This document presents a comprehensive overview of the testing conducted on the application, including various functionalities, defects found, reproduction steps, expected and current results, as well as their impact on system quality characteristics.

## Authentication (Login/Logout)

### Status
Minor Issues

### Defects Found
The application sometimes returns status code 201 instead of 200 during ping check.

### Reproduction Steps
1. Install the application according to the instructions provided.
2. Install testing tools.
3. Set up the environment for http://localhost:3001/ in POSTMAN.
4. Create a collection and request for Get/Ping - HealthCheck.
5. Copy the endpoint from the documentation: [Ping Documentation](https://restful-booker.herokuapp.com/ping)

### Expected Result
The application should return status code 200.

### Current Result
The application returns status code 201.

### Quality Characteristics
The application provides login and logout functionality but sometimes returns incorrect response codes, affecting system functionality.

### Remarks
Using code 200 "OK" directly indicates that the request has been successfully processed and the service is functioning correctly. Code 201 may introduce unnecessary confusion, suggesting that the operation had additional effects beyond just verifying availability. In the context of a "ping" operation, whose main purpose is to check the "health" of the application or its availability, code 200 "OK" is more appropriate and understandable for those making such checks.

## Booking Search (GetBooking)

### Status
Working

### Quality Characteristics
The application provides a booking search function that works correctly and meets user expectations.

## Booking Search by Name (GetBookingIds - Filter by name)

### Status
Not Working

### Defects Found
The application returns an empty response when a valid request is made.

### Reproduction Steps
1. Install the application according to the provided instructions.
2. Install testing tools.
3. Set up the environment for http://localhost:3001/ in POSTMAN.
4. Create a collection and request for Getbookingid - filter by name.
5. Copy the endpoint from the documentation: [Filter by Name Documentation](https://restful-booker.herokuapp.com/booking?firstname=sally&lastname=brown)

### Expected Result
According to the documentation, the application should return an array of objects containing unique booking identifiers.

### Current Result
The application returns empty content.

### Quality Characteristics
The booking search by name function does not work correctly, impacting system functionality.

## Booking Search by Date (GetBookingIds - Filter by date)

### Status
Not Working

### Defects Found
Incorrect behavior in searching by date for checkin.

### Reproduction Steps
1. Create a request POST booking - CreateBooking and create a new user.
2. Copy the endpoint from the documentation: [Filter by Date Documentation](https://restful-booker.herokuapp.com/booking)
3. Go to the request: GetBookingids (filter by date - checkin).
4. Set the parameter to "checkin" and the user's check-in date value.

### Current Result
Returns ID and reservations whose check-in date is greater than or equal to the set check-in date. The format must be CCYY-MM-DD.

### Expected Result
Current result: code 200. Return a list of IDs omitting the required ID.

### Quality Characteristics
Booking search by date does not work correctly, leading to incorrect results and reducing system functionality.

## Booking Search by Name (Filter by date - checkout)

### Status
Not Working

### Defects Found
Incorrect behavior in searching by date for checkout.

### Reproduction Steps
1. Copy the endpoint from the documentation: [Filter by Date - Checkout Documentation](https://restful-booker.herokuapp.com/booking)
2. Go to the request: GetBookingids (filter by date).
3. Set the parameter to "checkout" and the value: 2024-01-30.

### Current Result
Returns older dates than required in the documentation.

### Expected Result
The application should return reservations with checkout dates greater than or equal to the set checkout date. The format must be CCYY-MM-DD.

### Quality Characteristics
Booking search by date does not work correctly, leading to incorrect results and reducing system functionality.

## Creating a Booking (CreateBooking)

### Status
Working

### Quality Characteristics
The application allows the creation of new bookings, positively impacting system functionality.

## Creating a Booking (CreateBooking) without specifying the "totalprice" field

### Status
Not Working

### Defects Found
Receives error code 500 (Internal Server Error).

### Reproduction Steps
1. Go to / create request: POST: /booking - CreateBooking (JSON).
2. Go to the BODY and enter the necessary details.
3. Send the request.

### Current Result
Receives error code 500.

### Expected Result
The API should return response code 400 (Bad Request), preferably with a message explaining that the "totalprice" field is required.

### Remarks
According to the documentation, if the request is invalid or lacks required data, code 400 should be returned, informing the client of the error in their request.

### Quality Characteristics
Failure to create a booking without specifying the total price limits system functionality.

## Updating a Booking (UpdateBooking) using a token

### Status
Working

### Quality Characteristics
Successful booking update using a token providing secure operation authorization.

## Updating a Booking (UpdateBooking) using authorization

### Status
Not Working

### Defects Found
Application returns 403 Forbidden when using the Authorization header.

### Quality Characteristics
Authentication error during booking update limits system functionality.

## Attempting to update a booking without an authorization token (PUT)

### Status
Working

### Quality Characteristics
The application is protected against unauthorized modifications, positively impacting system functionality.

## Deleting a Booking (DeleteBooking) using a token

### Status
Minor Defects

### Defects Found
The application deletes bookings, but the returned status is code 201.

### Quality Characteristics
The application deletes bookings, but the returned status may be misleading to users.

## Deleting a Booking (DeleteBooking) using authorization

### Status
Not Working

### Defects Found
Application returns status code 405 Method not allowed.

### Quality Characteristics
The 405 Method not allowed error limits the ability to delete bookings.

## Conclusion

The application testing revealed several defects affecting various functionalities. These defects need to be addressed to ensure the system's functionality and maintain high-quality standards.

For further details on each functionality, including reproduction steps, expected and current results, please refer to the corresponding sections above.
