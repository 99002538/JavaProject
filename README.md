# JavaProject - Airline Reservation System  

---------------------------

|CI/CD|Codacy|Issues|Pull Requests|
|-----|-----|-----|-----|
|![Maven CI/CD](https://github.com/99002538/JavaProject/workflows/Maven%20CI/CD/badge.svg)| [![Codacy Badge](https://api.codacy.com/project/badge/Grade/69e8d1f222c74950a0cf35258d1569de)](https://app.codacy.com/gh/99002538/JavaProject?utm_source=github.com&utm_medium=referral&utm_content=99002538/JavaProject&utm_campaign=Badge_Grade)| ![GitHub open issues](https://img.shields.io/github/issues/99002538/JavaProject)|![GitHub closed pull requests](https://img.shields.io/github/issues-pr-closed-raw/99002538/JavaProject)|

---------------------------

### Brief description of implementation.

1) About coding.

    * Code environment: JAVA 8.
 
2) A few assumptions:

    * Suppose the price is integer. (Based on the summary example in the pdf file)

    * When book a passenger to a flight, suppose that the passenger choose a random seat.

    * Suppose one passenger book the same flight at most once.
    
       > For example, in inputfile2.txt "BookPassenger,RohanNeil,BOM,DXB" appears two times, 
       but we only book one ticket for RohanNeil for the flight "A769".
       
       > But for "BookPassenger,KennethHarris,CHI,DFW", since there are two flights, and the first time
       KennethHarris pick "K792" which has the lower price, the second time KennethHarris pick "A792"
       They are two different flights, thus we book two tickets for KennethHarris.

    * Suppose when the following scenario happens:
    
        > The passenger booked a flight at price 100
        
        > The flight changed price to 80.
        
        > The passenger request to book the flight the second time.
       In this case, the passenger's flight price is still 100, unless it cancel the flight and book again.

    * Suppose if a passenger booked two flights with the same origin and destination, if the passenger cancel
      a flight, then we should cancel the most expensive flight for the passenger.

    * Suppose only one type of passenger is considered here.

    * Suppose we use single thread to handle the transaction.

