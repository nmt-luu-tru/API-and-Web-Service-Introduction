### Understanding REST API Calls Through a Practical Example

Let’s dive into a practical example of how REST API calls work by exploring the process of interacting with the eBay Developers Program. Using RESTful APIs, we will make requests to the eBay sandbox environment, which is a test instance designed to allow developers to interact with eBay’s services without affecting live data.

#### Step 1: Obtaining an Access Token

Before we can interact with the API, we need an **access token**. The access token acts as a key that grants us permission to access the API’s resources.

1. **Get a Token**: Click on the "Get Token" link provided by the eBay Developers Program. This will generate an access token for the sandbox environment.
   
2. **Authorization**: The access token must be included in every API call we make. Typically, the token is passed in the header of the HTTP request using the `Authorization` header with the `Bearer` prefix. For example:

   ```
   Authorization: Bearer <access_token>
   ```

#### Step 2: Searching for Items Using the Browse API

We will start by performing a simple search for items with the word "computer" in their name using eBay’s **Browse API**.

1. **Define the API Endpoint**: 
   The endpoint for searching items is:
   ```
   https://api.sandbox.ebay.com/buy/browse/v1/item_summary/search
   ```
   
2. **Add Query Parameters**:
   We want to search for items that have "computer" in their name and retrieve only five results. The query parameter `q` is used to specify the search term, and `limit` is used to define the number of results. Thus, the complete endpoint becomes:

   ```
   https://api.sandbox.ebay.com/buy/browse/v1/item_summary/search?q=computer&limit=5
   ```
   
3. **Specify the HTTP Method**:
   We use the `GET` method to retrieve information. This is the most common method for fetching data from an API.

4. **Execute the Request**:
   We execute the request, and the server responds with a list of five items that have "computer" in their name.

#### Example Request and Response for Searching Items

- **Request**:
   ```
   GET https://api.sandbox.ebay.com/buy/browse/v1/item_summary/search?q=computer&limit=5
   Authorization: Bearer <access_token>
   ```

- **Response**:
   ```json
   {
       "total": 5,
       "itemSummaries": [
           {
               "itemId": "v1|1234567890|0",
               "title": "Computer Keyboard",
               "price": { "value": "25.00", "currency": "USD" },
               "itemWebUrl": "https://www.ebay.com/itm/computer-keyboard"
           },
           {
               "itemId": "v1|0987654321|0",
               "title": "Gaming Computer Mouse",
               "price": { "value": "45.00", "currency": "USD" },
               "itemWebUrl": "https://www.ebay.com/itm/gaming-computer-mouse"
           }
           // ... 3 more items
       ]
   }
   ```

The response includes a list of five items, each with attributes such as `itemId`, `title`, `price`, and `itemWebUrl`.

#### Step 3: Understanding the HTTP Request Structure

Each HTTP request consists of several key components:

1. **Start Line**:
   - Indicates the HTTP method (e.g., `GET`) and the target URL.
   
2. **Headers**:
   - Headers provide additional information about the request or response. For this example, headers include:
     - `Authorization: Bearer <access_token>`
     - `Content-Type: application/json` (if needed for other requests such as `POST` or `PUT`).
   
3. **Blank Line**:
   - A blank line separates the headers from the body.

4. **Body**:
   - In a `GET` request, there is typically no body. For `POST`, `PUT`, or `PATCH` requests, the body may contain data in JSON or other formats.

#### Step 4: Creating an Item Using the Inventory API

Let’s try creating an item using the **Inventory API**. This requires a `PUT` request because `PUT` is used to either create a new resource or replace an existing one.

1. **Define the Endpoint**:
   ```
   https://api.sandbox.ebay.com/sell/inventory/v1/inventory_item
   ```
   
2. **Specify the Request Body**:
   The request body should include details about the item, such as its name, quantity, and price. Here’s a basic example:

   ```json
   {
       "sku": "123456",
       "availability": {
           "shipToLocationAvailability": {
               "quantity": 10
           }
       },
       "product": {
           "title": "Example Product",
           "description": "An example product description",
           "aspects": {
               "Brand": ["Example Brand"],
               "Type": ["Electronics"]
           },
           "price": {
               "value": "99.99",
               "currency": "USD"
           }
       }
   }
   ```

3. **Execute the PUT Request**:
   When we try to execute the `PUT` request, we encounter an error:

   ```
   "message": "Insufficient permissions to fulfill the request."
   ```

   This error indicates that the token does not have the necessary permissions for creating or modifying inventory items. This highlights an important aspect of working with APIs: **understanding permissions and scopes**.

#### Step 5: Using Postman to Make REST API Calls

While eBay provides a web interface to interact with its APIs, using a tool like **Postman** allows us to view the underlying HTTP calls, which helps in debugging and understanding the API requests.

1. **Copy the Endpoint**:
   Copy the endpoint URL used earlier:
   ```
   https://api.sandbox.ebay.com/buy/browse/v1/item_summary/search?q=computer&limit=5
   ```

2. **Set Up the Authorization**:
   Use the `Bearer` token in the `Authorization` header:

   ```
   Authorization: Bearer <access_token>
   ```

3. **Send the Request**:
   Click on `Send` in Postman, and you should see a response similar to the one seen on eBay’s interface.

4. **Viewing the HTTP Request Code**:
   Postman provides a way to see the actual HTTP code being sent. Click on `Code` to view the generated HTTP request:

   ```http
   GET /buy/browse/v1/item_summary/search?q=computer&limit=5 HTTP/1.1
   Host: api.sandbox.ebay.com
   Authorization: Bearer <access_token>
   ```

This shows the complete HTTP request that was made, including the start line, headers, and parameters.

### Summary of Key Concepts

1. **Tokens and Authorization**:
   Accessing APIs requires tokens for authentication and authorization. Each API may require specific scopes for different operations.

2. **HTTP Methods**:
   RESTful APIs leverage standard HTTP methods (`GET`, `POST`, `PUT`, `DELETE`) to perform operations on resources.

3. **Request Structure**:
   Each HTTP request has a start line, headers, a blank line, and an optional body (depending on the method used).

4. **Error Handling**:
   Understanding error messages such as "Insufficient permissions" helps identify issues related to authorization, token scope, or endpoint access.

5. **Tools**:
   Using tools like Postman allows for detailed inspection and testing of API calls, making it easier to understand and troubleshoot.

By following these steps and understanding the components of REST API calls, you can effectively interact with various APIs and build robust integrations with external services.
