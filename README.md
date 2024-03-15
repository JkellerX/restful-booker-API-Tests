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

## Authentication (Login/Logout)

### Status
Minor Issues

### Defects Found
The application sometimes returns status code 201 instead of 200 during ping check.

### Reproduction Steps
1. Install the application according to the provided instructions.
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
Using code 200 "OK" directly indicates that the request has been successfully processed and the service is functioning correctly. Code 201 may introduce unnecessary confusion.

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
The application should return an array of objects containing unique booking identifiers.

### Current Result
The application returns empty content.

### Quality Characteristics
The booking search by name function does not work correctly, impacting system functionality.

## Booking Search by Date (GetBookingIds - Filter by date)

### Status
Not Working

### Defects Found
The application does not behave correctly when searching by date for check-in and check-out.

### Reproduction Steps
1. Copy the endpoint from the documentation: [Filter by Date Documentation](https://restful-booker.herokuapp.com/booking)
2. Create a request for GetBookingIds (filter by date - checkin or checkout).
3. Set the parameter for checkin or checkout and provide the desired date.

### Expected Result
The application should return bookings with check-in or check-out dates equal to or greater than the specified date.

### Current Result
The application returns incorrect dates.

### Quality Characteristics
The booking search by date function does not work correctly, impacting system functionality.

## Creating a Booking (CreateBooking)

### Status
Working

### Quality Characteristics
The application allows the creation of new bookings, positively impacting system functionality.

## Updating a Booking (UpdateBooking)

### Status
Working with Token / Not Working with Authorization

### Defects Found
The application successfully updates bookings using a token but returns a 403 Forbidden error when using Authorization.

### Quality Characteristics
The error in authorization during booking update restricts system functionality.

## Deleting a Booking (DeleteBooking)

### Status
Working with Token / Not Working with Authorization

### Defects Found
The application successfully deletes bookings using a token but returns a 405 Method not allowed error with Authorization.

### Quality Characteristics
The error 405 Method not allowed restricts the ability to delete bookings.

## Conclusion

The application testing revealed several defects affecting various functionalities. These defects need to be addressed to ensure the system's functionality and maintain high-quality standards.

For further details on each functionality, including reproduction steps, expected and current results, please refer to the corresponding sections above.
