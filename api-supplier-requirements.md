## API Supplier Requirements

1. The Supplier must provide an actual test environment or a test accommodation. The actual test environment has to be available within the entire validity of the Agreement.
 
2. The supplier API must behave according to provided documentation.

3. The Supplier should provide locality information in clear and unambiguous data format.\
The Supplier must provide the following data to an each accommodation:
    - Country name and/or ISO Alpha-2/Alpha-3 Country Code.
    - Locality name (city, settlement or other location of comparable scale).
    - For accommodations: GCS-compatible coordinates are mandatory.

4. The Supplier must inform Happy Travel IT team about API breaking changes or switching off the current version of an API for 2 months in advance.

5. The Supplier must provide a way to handle and recover a failed booking requests, e.g.:
    - Provide a reference number before an actual booking;
    - Disallow booking duplication.

6. Price of a booking mustn't change after a price evaluation step. The price evaluation has to be done before a booking process starts.

7. The final booking price must include all taxes and charges which are included in calculation between Happy Travel and the Supplier. 

8. All known additional ad-hoc costs and taxes should be shown in remarks.

9. Cancellation of a booking follows rules of a provided cancellation policy; Happy Travel ignores additional charges listed in remarks.

10. Happy Travel cannot guarantee the correct display of data which were supplied by free-format fields (i.e. cancellation policies in remarks or written by text instead of number, closed enumeration etc.).

11. Happy Travel cannot guarantee the correct data processing if the actual received data does not comply with supplier’s documentation.

12. The Supplier has to provide photos of hotels.

13. Execution time of a booking request must not exceed 60 seconds. If the time is more than 60 sec the booking is considered as failed.

14. In case of the Supplier caching the output between searching steps, the lifetime of responses must be not less than 10 minutes.

15. All responses for booking requests with HTTP codes other than 2XX are considered as failed.

16. The response of booking status should be clear and correct: cancel status means that booking is cancelled, confirmed status means that booking is confirmed, etc. 
The API is the main source of truth for the booking details and status.

17. All mandatory data (accommodations, amenities, board bases, localities, room descriptions and rates, cancellation policies, remarks) supplies in English. Multilanguage data is a plus.

18. Happy Travel reserves the right to use supplier’s data to improve its own products.
The Supplier must inform Happy Travel in advance, if Happy Travel is unable to use that data publicly or share it with third parties.

19. All interactions with the supplier API must run over the HTTPs protocol.

20. The Supplier should provide API limits in advance of an integration.

21. Status of the supplier’s system must be known, updated, and available by API within the entire validity of the Agreement. The supplier’s system must satisfy SLA 98 or better.
