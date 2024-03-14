
# Restful-booker-API-Tests

Restful-booker is a web API interface that allows for creating, reading, updating, deleting, equipped with authentication features and containing plenty of bugs for testing. The API comes pre-loaded with 10 records that you can work with, and it resets to its default state every 10 minutes. Restful-booker also includes detailed API documentation that will help you start testing the API right away. 
t is an open-source application that performs basic CRUD (Create, Read, Update, Delete) operations, which are actions of creating, reading, updating, and deleting data used in applications. Choosing such a system allows for demonstrating a range of different functionalities.

Sources:

-https://automationintesting.online - Preview site
-https://restful-booker.herokuapp.com/apidoc/index.html - Documentation
-https://github.com/mwinteringham/restful-booker - Public and free repository with installation instructions.

## Test Cases

### Authentication (Login/Logout)
**Status:** Minor Issues  
**Defects Found:** The application returns a status code 201 instead of 200 while checking the ping endpoint.  
**Quality Characteristics as per ISO 9126:**  
Functionality: The application provides login and logout functionality but sometimes returns an incorrect response code, affecting the system's functionality.

### GetBooking
**Status:** Working  
**No Defects Found.**  
**Quality Characteristics as per ISO 9126:**  
Functionality: The application provides a booking retrieval feature that works correctly and meets user expectations.

### GetBookingIds (Filter by name)
**Status:** Not Working  
**Defects Found:** The application returns an empty response after submitting a valid request.  
**Quality Characteristics as per ISO 9126:**  
Functionality: The feature to search bookings by name does not work correctly, affecting the system's functionality.

### GetBookingIds (Filter by date)
**Status:** Not Working  
**Defects Found:** Incorrect behavior when searching by check-in and check-out dates.  
**Quality Characteristics as per ISO 9126:**  
Functionality: Searching bookings by date does not work correctly, resulting in incorrect results and reduced system functionality.

### CreateBooking
**Status:** Working  
**No Defects Found.**  
**Quality Characteristics as per ISO 9126:**  
Functionality: The application allows creating new bookings, enhancing the system's functionality.

### CreateBooking without totalprice
**Status:** Not Working  
**Defects Found:** Receiving error code 500 (Internal Server Error) instead of 400.  
**Quality Characteristics as per ISO 9126:**  
Functionality: Error when creating a booking without specifying the total price limits the system's functionality.

### UpdateBooking using token
**Status:** Working  
**No Defects Found.**  
**Quality Characteristics as per ISO 9126:**  
Functionality: Successful booking update using a token ensures secure operation authorization.

### UpdateBooking using authentication
**Status:** Not Working  
**Defects Found:** Application returns 403 Forbidden when using the Authorization header.  
**Quality Characteristics as per ISO 9126:**  
Functionality: Authentication error during booking update limits system functionality.

### Attempting to update booking without authentication (PUT)
**Status:** Working  
**No Defects Found.**  
**Quality Characteristics as per ISO 9126:**  
Functionality: Application secured against unauthorized modifications, enhancing system functionality.

### DeleteBooking using token
**Status:** Minor Defects  
**Defects Found:** The application deletes bookings, but the returned status is 201.  
**Quality Characteristics as per ISO 9126:**  
Functionality: The application deletes bookings, but the returned status can be misleading for users.

### DeleteBooking using authentication
**Status:** Not Working  
**Defects Found:** Application returns status code 405 Method Not Allowed.  
**Quality Characteristics as per ISO 9126:**  
Functionality: Error 405 Method Not Allowed limits the ability to delete bookings.