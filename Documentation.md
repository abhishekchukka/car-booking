# Cab Booking System Documentation

## Project Overview

The Cab Booking System is a Java-based application designed to facilitate the booking of cabs by riders. The system allows riders to register, book rides, and view their ride history, while drivers can register, update their availability, and manage their cab locations. The application aims to provide a seamless experience for both riders and drivers, ensuring efficient ride management and tracking.

---

## Class Descriptions

### 1. Class: `CabManager`

**Description:** Manages drivers, their statuses, locations, and active rides. It tracks available cabs and updates their statuses during rides.

#### Key Fields

- `Map<String, Driver> driverDetails`: Stores driver details with their unique IDs as keys.
- `Map<String, String> cabStatus`: Stores the status of each cab (e.g., available, on ride).
- `Map<String, Location> driverLocations`: Stores the current locations of drivers.
- `Map<String, RideDetails> activeRides`: Stores active rides associated with riders.

#### Methods

- `void addOrUpdateCabLocation(String id, Location location)`

  - **Description:** Adds or updates the location of a cab.
  - **Parameters:**
    - `String id`: The unique ID of the driver.
    - `Location location`: The new location of the cab.

- `void updateCabStatus(String id, String status)`

  - **Description:** Updates the status of a cab (e.g., free, on ride).
  - **Parameters:**
    - `String id`: The unique ID of the driver.
    - `String status`: The new status of the cab.

- `Driver getAvailableCabs(Location userLocation)`

  - **Description:** Retrieves a list of available cabs based on the rider's location.
  - **Parameters:**
    - `Location userLocation`: The location of the rider.
  - **Returns:** `Driver` - The nearest available driver.

- `void registerDriver(Driver d)`

  - **Description:** Registers a new driver in the system.
  - **Parameters:**
    - `Driver d`: The driver to be registered.

- `Map<String, RideDetails> getActiveRides()`
  - **Description:** Returns a map of active rides.
  - **Returns:** `Map<String, RideDetails>` - A map of active rides.

---

### 2. Class: `BookingManager`

**Description:** Handles the booking and ending of rides. Interfaces with `CabManager` to update ride status and manage driver availability.

#### Methods

- `RideDetails bookRide(Rider rider, Driver driver, Location riderLocation, Location destination)`

  - **Description:** Books a ride for a rider with a selected driver.
  - **Parameters:**
    - `Rider rider`: The rider booking the ride.
    - `Driver driver`: The driver assigned to the ride.
    - `Location riderLocation`: The current location of the rider.
    - `Location destination`: The destination of the ride.
  - **Returns:** `RideDetails` - The details of the booked ride.

- `void endRide(RideDetails rideDetails, RiderManager rm)`
  - **Description:** Ends the ride and updates the ride history.
  - **Parameters:**
    - `RideDetails rideDetails`: The details of the ride to be ended.
    - `RiderManager rm`: The rider manager to update ride history.

---

### 3. Class: `Driver`

**Description:** Represents a cab driver.

#### Key Fields

- `String id`: A unique identifier for the driver.
- `String name`: The name of the driver.
- `Car car`: The car associated with the driver.

#### Methods

- `Driver()`

  - **Description:** Constructor that initializes the driver with a unique ID.

- `void registerDriverWithCar(String name, int licenseNumber, Car car)`

  - **Description:** Registers the driver with their name and car details.
  - **Parameters:**
    - `String name`: The name of the driver.
    - `int licenseNumber`: The driver's license number.
    - `Car car`: The car associated with the driver.

- `String getName()`

  - **Description:** Returns the driver's name.
  - **Returns:** `String` - The name of the driver.

- `String getID()`
  - **Description:** Returns the driver's unique ID.
  - **Returns:** `String` - The ID of the driver.

---

### 4. Class: `Rider`

**Description:** Represents a rider who books a cab.

#### Key Fields

- `String id`: A unique identifier for the rider.
- `String name`: The name of the rider.

#### Methods

- `Rider(String name)`

  - **Description:** Constructor that initializes the rider with a unique ID and name.
  - **Parameters:**
    - `String id`: The unique ID of the rider.
    - `String name`: The name of the rider.

- `String getName()`

  - **Description:** Returns the rider's name.
  - **Returns:** `String` - The name of the rider.

- `String getID()`
  - **Description:** Returns the rider's unique ID.
  - **Returns:** `String` - The ID of the rider.

---

### 5. Class: `Location`

**Description:** Represents coordinates (x, y) for drivers and riders.

#### Key Fields

- `int x`: The x-coordinate of the location.
- `int y`: The y-coordinate of the location.

#### Methods

- `Location(int x, int y)`

  - **Description:** Constructor to create a location with specific coordinates.
  - **Parameters:**
    - `int x`: The x-coordinate of the location.
    - `int y`: The y-coordinate of the location.

- `int getX()`

  - **Description:** Returns the x-coordinate of the location.
  - **Returns:** `int` - The x-coordinate of the location.

- `int getY()`

  - **Description:** Returns the y-coordinate of the location.
  - **Returns:** `int` - The y-coordinate of the location.

- `double calculateDistance(Location other)`

  - **Description:** Calculates the distance between the current location and another location using the Euclidean distance formula.
  - **Parameters:**
    - `Location other`: The other location to calculate the distance to.
  - **Returns:** `double` - The calculated distance.

- `String toString()`
  - **Description:** Returns a string representation of the location.
  - **Returns:** `String` - The string representation of the location.

---

### 6. Class: `RideDetails`

**Description:** Captures details of a ride, including the rider, driver, distance, and amount.

#### Key Fields

- `Rider rider`: The rider associated with the ride.
- `Driver driver`: The driver assigned to the ride.
- `double distance`: The distance of the ride.
- `double amount`: The fare amount for the ride.

#### Methods

- `RideDetails(Rider rider, Driver driver, double distance, double price)`

  - **Description:** Constructor to initialize ride details.
  - **Parameters:**
    - `Rider rider`: The rider for the ride.
    - `Driver driver`: The driver for the ride.
    - `double distance`: The distance of the ride.
    - `double price`: The price of the ride.

- `Rider getRider()`

  - **Description:** Retrieves the rider associated with the ride.
  - **Returns:** `Rider` - The rider associated with the ride.

- `Driver getDriver()`

  - **Description:** Retrieves the driver associated with the ride.
  - **Returns:** `Driver` - The driver associated with the ride.

- `double getDistance()`

  - **Description:** Retrieves the distance of the ride.
  - **Returns:** `double` - The distance of the ride.

- `double getPrice()`

  - **Description:** Retrieves the fare price of the ride.
  - **Returns:** `double` - The fare price of the ride.

- `void setPrice(double price)`

  - **Description:** Sets the fare price of the ride.
  - **Parameters:**
    - `double price`: The new fare price.

- `void setDistance(double distance)`

  - **Description:** Sets the distance of the ride.
  - **Parameters:**
    - `double distance`: The new distance of the ride.

- `String getRideDetails()`
  - **Description:** Retrieves the details of the ride as a string.
  - **Returns:** `String` - A string representation of the ride details.

---

### 7. Class: `RiderManager`

**Description:** Manages riders, their details, and ride history.

#### Methods

- `void setRiderDetails(Rider rider)`

  - **Description:** Sets the details of a rider for a ride.
  - **Parameters:**
    - `Rider rider`: The rider whose details are to be set.

- `void updateRiderLocation(Rider rider, Location location)`

  - **Description:** Updates the location of a rider.
  - **Parameters:**
    - `Rider rider`: The rider whose location is to be updated.
    - `Location location`: The new location of the rider.

- `void addRideToHistory(Rider rider, RideDetails rideDetails)`
  - **Description:** Adds a completed ride to the rider's history.
  - **Parameters:**
    - `Rider rider`: The rider whose ride history is to be updated.
    - `RideDetails rideDetails`: The details of the ride to be added.
    -

---

# 8. Class: `DefaultAssignmentStrategy`

**Description:** Implements the assignment strategy for selecting the most suitable driver based on proximity to the rider's location.

### Methods:

- **Driver assignDriver(List<Driver> availableDrivers, Location user, Map<String, Location> driverLocations):**
  - **Description:** Assigns a driver to a rider based on the available drivers and the rider's location.
  - **Parameters:**
    - `List<Driver> availableDrivers`: A list of drivers who are currently available.
    - `Location user`: The location of the rider.
    - `Map<String, Location> driverLocations`: A map containing the locations of all drivers.
  - **Returns:** `Driver` - The driver who is the nearest to the rider.

---

# 9. Class: `BasicPriceCalculator`

**Description:** Provides a basic pricing calculation for a ride based on the distance traveled.

### Methods:

- **double calculatePrice(double distance):**
  - **Description:** Calculates the price of a ride based on the distance traveled by the rider.
  - **Parameters:**
    - `double distance`: The distance of the ride in kilometers.
  - **Returns:** `double` - The calculated price based on the distance.

---

# 10. Class: `RiderTester`

**Description:** Used for testing the functionality of the cab booking system, including driver assignment and ride booking.

### Methods:

- **static void setupDrivers(CabManager cabManager):**

  - **Description:** Sets up initial driver details in the `CabManager`.
  - **Parameters:**
    - `CabManager cabManager`: The manager that handles driver registration and updates.

- **public static void main(String[] args):**
  - **Description:** The main method for running the testing application. It interacts with the cab booking system to simulate rider and driver activities.
  - **Parameters:**
    - `String[] args`: Command-line arguments.
  - **Returns:** `void`

---

# 11. Interface: `AssignmentStrategy`

**Description:** Defines the strategy for assigning drivers to riders. Different strategies can be implemented to change how the driver is selected.

### Methods:

- **Driver assignDriver(List<Driver> availableDrivers, Location user, Map<String, Location> driverLocation):**
  - **Description:** Assigns a driver to a rider based on a specific strategy.
  - **Parameters:**
    - `List<Driver> availableDrivers`: A list of available drivers.
    - `Location user`: The location of the rider.
    - `Map<String, Location> driverLocation`: A map containing the locations of all drivers.
  - **Returns:** `Driver` - The assigned driver based on the chosen strategy.

---

## Sample Outputs

### Successful Ride Booking and Completion

```java
Choose an option:
1. Add Rider and Book Ride
2. End a Ride
3. View Ride History
4. Exit

1
Enter Rider Name: alas
Rider alas added successfully.
Enter Rider's Current X Location: 10
Enter Rider's Current Y Location: 10
[Driver@0717ecd, Driver@66a29884]
Selected Driver: Driver1
Enter Destination X Location: 30
Enter Destination Y Location: 30
Ride Began -> Rider: alas, Driver: Driver1, Distance: 28.28 km, Price: $282.84
Ride booked successfully for Rider: alas
```

### Ending a Ride

```java
Choose an option:
2
Enter Rider Name to End the Ride: abhi
Ride ended: Rider: abhi had a cab trip with Driver: Driver2 for a fare: $28.28 over 2.828 km.
Ride ended for Rider: abhi
```

### Viewing Ride History

```java
Choose an option:
3
Enter Rider Name to View Ride History: abhi
Ride History for Rider: abhi
Rider: abhi had a cab trip with Driver: Driver2 for a fare: $28.28 over 2.828 km.
```

---

## Assumptions

1. **Drivers' Availability:** Drivers are initially marked as "available" upon registration.
2. **Riders' Locations:** Riders provide accurate `(x, y)` coordinates for their location and destination.
3. **Fare Calculation:** Fares are calculated as `$10 per kilometer`.
4. **Ending Rides:** A ride must be ended manually by selecting the appropriate option in the menu.

---

## Future Enhancements

1. **Multi-Ride Handling:** Allow drivers to accept multiple ride requests in sequence.
2. **Real-Time Location Tracking:** Integrate with mapping APIs to provide real-time cab tracking.
3. **Automated Fare Payment:** Implement automated fare calculations and digital payment options.
4. **Driver Rating System:** Allow riders to rate drivers after each ride to improve service quality.

---
