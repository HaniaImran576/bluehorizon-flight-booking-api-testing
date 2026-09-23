# BlueHorizon Flight Booking Module - API Testing

A Postman based API test suite covering the flight booking module of BlueHorizon, a full travel booking platform I built in my 4th semester that also includes hotels, destinations, and packages. This project revisits that module specifically to test it end to end, the way I would test something built for a real client rather than for a grade.

## Scope
This project covers only the flight booking module. Hotel and package booking share similar authentication and checkout logic and are planned as a future extension, not included here.

## What's Covered
The collection follows the full user journey for flight booking, chained together in sequence rather than tested as isolated, disconnected requests:

1. Signup
2. Login
3. Retrieve Flights
4. Add to Cart
5. View Cart
6. Checkout

Each request includes assertions that check not just the HTTP status code, but that the response actually contains what it should: the account created correctly, flights returned in the right structure, the seat added to cart, cart contents accurate, and checkout returning a proper confirmation.

## Why Chained Requests
A user does not hit checkout in isolation. They sign up, log in, browse flights, and build a cart first. Testing each step separately would not reveal whether the full journey actually holds together, for example whether the session created at login correctly carries through to checkout. Chaining these requests in one sequence tests that continuity directly.

## Results
| Metric | Result |
|---|---|
| Total assertions | 12 |
| Passed | 12 |
| Failed | 0 |
| Average response time | approximately 10ms |

All 12 assertions passed across the full signup through checkout flow.

## Tools
- Postman, for building and running the collection

## How to Run
1. Import `BlueHorizon-Flight-Booking.postman_collection.json` into Postman.
2. Set up an environment with your own BlueHorizon instance base URL, since this project was tested against a personal semester project rather than a publicly hosted API.
3. Run the collection in sequence (Runner or manually, request by request) so that data created in earlier steps, such as the signed up account and cart contents, carries through correctly to later steps.

## Next Steps
- Add negative test cases to this same flow: signup with an already used email, login with incorrect credentials, and checkout attempted with an empty cart.
- Extend this same chained testing approach to the hotel and package booking modules, since they likely share similar authentication and checkout logic.
