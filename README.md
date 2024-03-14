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

# Protocol of Conducted Tests

Here is a list of the main functionalities of the Restful-Booker application:

1. **Authentication (Login/Logout):** Users can log in to the system by providing correct authentication data, and log out to end the session.

2. **Booking Search (GetBooking):** Allows users to retrieve detailed information about existing bookings.

3. **Booking Search by Name (GetBookingIds - Filter by name):** Enables searching for bookings based on the user's name or other criteria.

4. **Booking Search by Date (GetBookingIds - Filter by date):** Allows filtering bookings based on the check-in and check-out dates.

5. **Creating a New Booking (CreateBooking):** Users can make a new booking by providing required data such as first name, last name, check-in and check-out dates, and other details.

6. **Updating an Existing Booking (UpdateBooking):** Allows users to update existing bookings, such as changing the check-in or check-out dates.

7. **Deleting a Booking (DeleteBooking):** Enables users to delete existing bookings from the system.

## Conducted Tests and Found Defects

1) **Authentication (Login/Logout)**

   **Status:** MINOR ISSUES  
   **Found Defects:** During the ping check, the application returns code 201 instead of 200.  
   
   -Steps to Reproduce:
  > 1. Install the application according to the instructions available above.
  > 2. Install the testing tool.
  > 3. Create an environment for http://localhost:3001/ in POSTMAN.
  > 4. Create a collection and request for Get/Ping - HealthCheck.
  > 5. Copy the endpoint from the documentation https://restful-booker.herokuapp.com/ping
   
   **Expected Result:** The application should return code 200.
   **Actual Result:** The application returns code 201.
   
   **Quality Characteristics:**
   - Functionality: The application provides the function of logging in and logging out, but sometimes returns an incorrect response code, affecting the system's functionality.

3) **Booking Search (GetBooking)**

   **Status:** WORKING  
   **No defects found.**  
   
   **Quality Characteristics according to ISO 9126:**  
   - Functionality: The application provides a booking search function that works correctly and meets user expectations.

3) **Booking Search by Name (GetBookingIds - Filter by name)**

   **Status:** NOT WORKING  
   **Found Defects:** The application returns an empty response after submitting a valid request.  
   
   **Description:**
   The application returns an empty response after submitting a valid request for "Check-in" search.  
   
   -Steps to Reproduce:
   >1. Install the application according to the instructions available above.
   >2. Install the testing tool.
   >3. Create an environment for http://localhost:3001/ in POSTMAN.
   >4. Create a collection and request for Getbookingid - filter by name).
   >5. Copy the endpoint from the documentation -https://restful-booker.herokuapp.com/booking?firstname=sally&lastname=brown
   
   **Expected Result:**
   According to the documentation, the application should return an array of objects containing unique booking identifiers.
   
   **Actual Result:**
   The application returns an empty response.
   
   **Quality Characteristics according to ISO 9126:**
   - Functionality: The function of searching for bookings by name does not work correctly, affecting the system's functionality.