- [[#Testing `flightBookingQuery`|Testing `flightBookingQuery`]]
- [[#Testing `purchaseBooking`|Testing `purchaseBooking`]]
- [[#Test Suite|Test Suite]]
- [[#Initializing Airports|Initializing Airports]]
- [[#Initializing Flights|Initializing Flights]]
- [[#Initializing Bookings|Initializing Bookings]]
- [[#Initializing All Flights|Initializing All Flights]]


With `BackEnd.h` now provided, you can get a clearer picture of what functions you're supposed to test. You're essentially responsible for ensuring that the `flightBookingQuery` and `purchaseBooking` functions behave as specified. Given the restrictions, it looks like you're expected to focus solely on writing test cases for these functions in `UnitTests.cpp`.

Here are some test scenarios that should cover the specifications:

### Testing `flightBookingQuery`

1. **Basic Scenario: Direct Flights**
    
    - Create multiple `Flight` objects with the same source and destination airports.
    - Call `flightBookingQuery` and check that you get back Bookings with the right Flights, sorted by departure time.
2. **Flight Capacity**
    
    - Create a `Flight` object with zero capacity.
    - Call `flightBookingQuery` and check that this flight is not part of any returned Booking.
3. **Connecting Flights**
    
    - Create multiple `Flight` objects such that there are no direct flights between source and destination, but there are connecting options.
    - Call `flightBookingQuery` and ensure it returns Bookings with connecting flights.
4. **Departure Time for Connecting Flights**
    
    - Create a scenario where the second flight in a connecting flight pair leaves less than 2 hours after the first flight’s departure.
    - Call `flightBookingQuery` and ensure this pair does not appear in any Booking.

### Testing `purchaseBooking`

1. **Decrease Capacity**
    
    - Create a Booking and call `purchaseBooking`.
    - Ensure the capacity of all the Flights in that Booking is decremented.
2. **Post-Purchase Availability**
    
    - Purchase a Booking and then call `flightBookingQuery` to ensure the capacities are updated as expected (e.g., a flight that's now full isn't available anymore).

### Test Suite

Your `UnitTests.cpp` would instantiate the needed `Airport`, `Flight`, and `Booking` objects, and then assert these conditions using your testing framework. Since you're not allowed to modify anything other than `UnitTests.cpp`, the testing needs to be self-contained.

To ensure your tests are robust, you might consider edge cases like only one flight being available, the same flight being part of multiple bookings, etc.

### Initializing Airports

You can initialize Airport objects using their constructor, which expects a 3-letter airport code.


`Airport source("JFK"); Airport destination("LAX");`

### Initializing Flights

Flights require a capacity, a takeoff time, and references to the source and destination Airports.

`Flight flight1(100, 9, source, destination);  // 100 available seats, departs at 9:00 Flight flight2(100, 12, source, destination); // 100 available seats, departs at 12:00`

### Initializing Bookings

Bookings require a vector of `Flight` pointers.


`std::vector<Flight*> flights_for_booking1 = { &flight1 }; std::vector<Flight*> flights_for_booking2 = { &flight1, &flight2 };  Booking booking1(flights_for_booking1); Booking booking2(flights_for_booking2);`

### Initializing All Flights

You might want to initialize a vector containing all the flights available for the test.

`std::vector<Flight*> allFlights = { &flight1, &flight2 };`

After initializing these objects, you can call your methods under test (`flightBookingQuery` and `purchaseBooking`) and make assertions based on the expected behavior.

Here's how you might call `flightBookingQuery`:


`std::vector<Booking> available_bookings = flightBookingQuery(allFlights, source, destination);`

And to call `purchaseBooking`:

`purchaseBooking(booking1);`

You can then follow up these calls with assertions to check whether the method's behavior aligns with the expectations set out in the project's specification