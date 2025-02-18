This is a Express.js-based test bench API designed to simulate various scenarios such as delays, errors, CRUD operations, status codes, instance chaining, and load simulation. It uses an in-memory SQLite database for CRUD operations.

Delay Simulation: Simulate delayed responses.

Error Simulation: Simulate both fatal and handled errors.

CRUD Operations: Perform Create, Read, Update, and Delete operations on an in-memory SQLite database.

Status Code Simulation: Simulate different HTTP status codes.

Instance Chaining: Chain requests to multiple instances.

Load Simulation: Simulate API load by making multiple requests concurrently.

INSTALLATION:
Ensure Node.js and npm installed.
npm init -y
npm install express 
npm install express sqlite3 axios

API ENDPOINTS:
1. Delay Simulation
Endpoint: /delay
Method: GET
Query Parameters:
delay: The delay in milliseconds
URL: http://localhost:3000/delay?delay=2000

2. Error Simulation
Endpoint: /error
Method: GET
Query Parameters:
type: Type of error to simulate (fatal or handled).
Triggers different types of errors or no error based on query parameter.
Fatal Error: http://localhost:3000/error?type=fatal
Handled Error: http://localhost:3000/error?type=handled
No Error: http://localhost:3000/error

3. CRUD Operations
Endpoint: /crud
Method: POST
Create Only: curl -X POST http://localhost:3000/crud -H "Content-Type: application/json" -d '{"operation": "C"}'
Create & Read: curl -X POST http://localhost:3000/crud -H "Content-Type: application/json" -d '{"operation": "CR"}'
Create, Read & Update: curl -X POST http://localhost:3000/crud -H "Content-Type: application/json" -d '{"operation": "CRU"}'
Full CRUD (Create, Read, Update, Delete): curl -X POST http://localhost:3000/crud -H "Content-Type: application/json" -d '{"operation": "CRUD"}'
Description: Executes CRUD operations based on the string provided (C, CR, CRU, CRUD).

4. Status Code Simulation
Endpoint: /status/:code
Method: GET
Path Parameters: code: The HTTP status code to simulate.
URL: http://localhost:3000/status/404
Simulates HTTP status codes by responding with the given error code.

5. Instance Chaining
Endpoint: /chain
Method: GET
Query Parameters: seq: Comma-separated list of instance indices to chain (default: 1,2,3,4).
URL: http://localhost:3000/chain?seq=1,2,3,4
Calls the given sequence of instances (/instance1, /instance2, etc.)

6. Load Simulation
Endpoint: /simulate-load
Method: GET
URL: http://localhost:3000/simulate-load
Simulates API load by making multiple automated requests. responses from multiple endpoints (/delay, /error, /crud).

7. Default Instances
Endpoints: /instance1, /instance2, /instance3, /instance4
Method: GET
URL: http://localhost:3000/instance1




