# Implementation

   * Class, data structure and logic: 
   
      - **Flight**: information about flight, contains flight basic information and reservation.
      
               1. Member of the class: 
                        Flight number, 
                        Total number of seats in flight,
                        Price per seat.
                        Origin code
                        Destination code
                        Flight reservation list
                        Seat pool, stored as LinkedList.
               2. HashMap<Passenger, ReservationItem> to store all reservation on this flight
               3. LinkedList<Integer> to store all available seats and generate random seats for reservation.
               4. Each time there is a BookPassenger happens, a ReservationItem will be created and stored into
                  this HashMap<Passenger, ReservationItem>. And at the same time we remove the random generated 
                  seat from LinkedList<Integer> seat pool.
               5. Each time there is a CancelPassenger happens, we remove ReservationItem from Map and restore the 
                  seat to LinkedList<Integer> seat pool.
               6. When changePrice happens, we update the price of the flight.

      - **FlightReservationSystem**: store all flights information and handle transactions.
      
               1. HashMap<OriginDestinationPair, TreeSet<Flight>>, to store all the flights have the same origin and 
                  destination. Use a TreeSet to keep the order of the flights, it is sorted by the flight price, thus 
                  it enables us to choose the cheapest flight for the passenger.
               2. HashMap<String, Flight> flightNumberToFlightMap, enable us to fast get a flight by flight number.
               3. When process BookPassenger transaction, we first find all flights by origin and destination. Then 
                  choose a cheapest available flight for passenger.
               4. When process CancelPassenger, we cancel the most expensive flight for passenger.
               5. When changePrice, we change the price of the flight and reorder the flights TreeSet. 

      - **SystemRunner**: entrance of program, to process transactions and create report.
      - **FlightInCSVIndexEnum**: Enum of flight's columns index in CSV file. For example, Flight number is at 
        the first column, thus it's index is 0.
      - **FlightSummary**: contains a flight's total avenue, available seats, etc.
      - **OriginDestinationPair**: contains Origin and Destination.
      - **Passenger**: passenger information, contains passenger name.
      - **ReservationItem**: a reservation on a flight, contains passenger, seat number, price.
      - **TransactionTypeEnum**: transaction type, contains: book, cancel and change price.
