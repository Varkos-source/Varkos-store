# API Documentation

## Authentication

### Endpoints

- **POST /auth/login**  
  Authenticate a user and return a token.
  - **Request Body:**  
    - `email`: User's email.
    - `password`: User's password.
  - **Response:**  
    - `token`: JWT token for subsequent requests.

- **POST /auth/register**  
  Create a new user account.
  - **Request Body:**  
    - `name`: User's name.
    - `email`: User's email.
    - `password`: User's password.
  - **Response:**  
    - `message`: Success message.

---

## Products

### Endpoints

- **GET /products**  
  Fetch a list of all products.
  - **Response:**  
    - `products`: Array of product objects with details (id, name, price, etc).

- **GET /products/{id}**  
  Get detailed information about a specific product.
  - **Response:**  
    - `product`: Object with detailed product information.

- **POST /products**  
  Add a new product to the catalog. (Requires authentication)
  - **Request Body:**  
    - `name`: Product name.
    - `price`: Product price.
    - `description`: Product description.
    - `image`: Product image URL.
  - **Response:**  
    - `message`: Success message.

---

## Cart

### Endpoints

- **GET /cart**  
  Retrieve the current user's shopping cart.  
  - **Response:**  
    - `cart`: Object containing cart details (items, total cost, etc).

- **POST /cart/add**  
  Add an item to the user's cart.  
  - **Request Body:**  
    - `productId`: ID of the product to add.
    - `quantity`: Quantity of the product.
  - **Response:**  
    - `message`: Success message.

- **DELETE /cart/remove/{productId}**  
  Remove an item from the user's cart.  
  - **Response:**  
    - `message`: Success message.

---

## Orders

### Endpoints

- **POST /orders**  
  Create a new order. (Requires authentication)
  - **Request Body:**  
    - `cartId`: ID of the user's cart.
    - `shippingAddress`: Address to ship the order.
  - **Response:**  
    - `orderId`: ID of the created order.
    - `message`: Success message.

- **GET /orders/{id}**  
  Retrieve details of a specific order.
  - **Response:**  
    - `order`: Object with order details.

- **GET /orders**  
  Get a list of all orders for the authenticated user.
  - **Response:**  
    - `orders`: Array of user orders.

---

## Notes
- Ensure to replace `{id}` and `{productId}` with actual values when making requests.
- All authentication-required endpoints must be accompanied by a valid JWT token in the request header.