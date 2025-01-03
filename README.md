**Project Overview**

This repository contains API tests for the Cart Module of the OpenCart application, implemented using Postman. 

The project includes API chaining, dynamic variable handling, and comprehensive validations to ensure accurate testing of cart-related 

operations like adding, updating, retrieving, and removing products.



**Key Features**

**Collection Variables:**

ip and baseurl are stored at the collection level to simplify URL management across requests.

**API Chaining:**

Extracted api_token from the session creation response and reused it for all subsequent requests for Authorization

Extracted cart_id from the Get Cart Content request and reused it in Edit and Remove operations.

**Dynamic Scripting:**

Scripts were used to validate responses and store dynamic data as collection variables.

**Comprehensive Validation:**

Response codes and messages were validated for all requests in the Postman test scripts.



**Prerequisites**

Ensure you have the following:

Postman: Installed on your system.

XAMPP: Installed to run OpenCart locally.

OpenCart: Frontend and backend applications downloaded and configured.


**Setting Up OpenCart**


1. Download OpenCart

   Visit the official OpenCart download page.

   Download the latest version of OpenCart.


2. Install XAMPP

   Download XAMPP from the official website.

   Install XAMPP and launch the Control Panel.

   Start the Apache and MySQL modules.


3. Set Up OpenCart in XAMPP

   Extract the downloaded OpenCart archive.

   Copy the extracted files into the htdocs folder of your XAMPP installation directory (e.g., C:\xampp\htdocs\opencart).

   Open a web browser and navigate to http://localhost/opencart/ to begin the installation wizard.

   Follow the on-screen instructions to configure:

   Database Connection: Provide MySQL credentials (default: username root and no password).

   Admin Credentials: Set up an admin username and password for the OpenCart backend.

   After installation, access the OpenCart backend at http://localhost/opencart/admin.



4. Configure API User

   Log in to the OpenCart backend.

   Navigate to System > Users > API.

   Add a new API user with a username (e.g., test_user) and generate an API key.

   Enable the API user and save the changes.

   Ensure the IP address of your testing machine is added to the allowed IP list for the API.


**Project Structure**

opencart-api-testing/

│

├── OpencartCollection.json

│   ├──   POST create new session

│   ├──   POST Add product to the cart

│   ├──   GET Get cart content

│   ├──   POST Edit product quantity in the cart

│   └──  POST Remove product from cart



**API Endpoints and Workflow**

**Create Session**

Endpoint: /api/login

Method: POST

Request Body: API username and API key.

Workflow: 

Validate response code and message.

Extract api_token from the response body and store it as a collection variable.

**Add Product to Cart**

Endpoint: /api/cart/add

Method: POST

Authorization: api_token.

Request Body: product_id and quantity.

Workflow:

Validate response code and message.

**Get Cart Content**

Endpoint: /api/cart/products

Method: GET

Authorization: api_token.

Workflow:

Validate response code.

Extract cart_id from the Response body and store it as a collection variable.

**Edit Product Quantity**

Endpoint: /api/cart/edit

Method: POST

Authorization: api_token.

Request Body: cart_id and new quantity.

Workflow:

Validate response code and message.

**Remove Product from Cart**

Endpoint: /api/cart/remove

Method: POST

Authorization: api_token.

Request Body: cart_id.

Workflow:

Validate response code and message.

Cleanup

All collection variables are unset after tests are completed.

**Running the Tests**

Postman GUI:

Import the collection and environment files.

Configure variables like baseurl and ip.

Execute the collection.

**Newman CLI:**

Install Newman:

    npm install -g newman

Install Newman Reporter HTML

    npm install -g newman-reporter-html

Run the collection:

    newman run OpencartCollection.json.json 

Generate HTML Report

    newman run OpencartCollection.json -r html


**Report Screenshots**

**Report1**

![Opencart ss1](Opencart%20screenshots/Opencart%20ss1.PNG)

**Report2**

![Opencart ss2](Opencart%20screenshots/Opencart%20ss2.PNG)

**Report3**

![Opencart ss3](Opencart%20screenshots/Opencart%20ss3.PNG)





