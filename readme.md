## Spice Safari Backend API Documentation

Welcome to the backend API documentation for Spice Safari, a food ordering application. This Node.js, Express, MongoDB, and TypeScript-based backend provides functionalities for user authentication, product management, cart handling, order processing, and admin actions.

**Postman Documentation:**

Explore the detailed API documentation for testing and interacting with the Spice Safari backend using Postman: [Link to Postman Documentation](link_to_postman_documentation)

**Features and Endpoints:**

**User Authentication:**

* **Register User:**
    * Endpoint: `POST /user/register`
    * Description: Users can create accounts with their email address, password, and full name.
    * Body:
        * `email`: User's email address (required)
        * `password`: User's password (required)
        * `fullName`: User's full name (required)
* **Login User:**
    * Endpoint: `POST /user/login`
    * Description: Users can log in to their accounts with their email address and password.
    * Body:
        * `email`: User's email address (required)
        * `password`: User's password (required)
* **Logout User:**
    * Endpoint: `GET /user/logout`
    * Description: Users can log out of their accounts. (Requires User Authentication)

**Product Management:**

* **View All Products:**
    * Endpoint: `GET /product/`
    * Description: Retrieve a list of all available products.
    * Access: Public (Anyone can access)
* **Get Single Product:**
    * Endpoint: `GET /product/:id`
    * Description: Users can view details of a specific product.
    * Access: Public (Anyone can access)
* **Wishlist Product:**
    * Endpoint: `PATCH /user/:userId/wishlist/:productId`
    * Description: Users can add products to their wishlist. (Requires User Authentication)
    * Body:
        * `userId`: User's ID (required)
        * `productId`: Product's ID (required)

**Admin-only functionalities require Admin Authentication (refer to Admin Authentication section).**

* **Create Product:**
    * Endpoint: `POST /product/create`
    * Description: Admins can add new products to the catalog.
    * Body: (multipart/form-data)
        * `name`: Product name (required)
        * `description`: Product description (required)
        * `price`: Product price (required)
        * `category`: Product category (required)
        * `photo`: Product image (required) (image file)
* **Update Product:**
    * Endpoint: `PATCH /product/:id`
    * Description: Admins can update product information.
    * Body: (multipart/form-data) (optional fields only)
        * `name`: Product name
        * `description`: Product description
        * `price`: Product price
        * `category`: Product category
        * `photo`: Product image (image file)
* **Delete Product:**
    * Endpoint: `DELETE /product/:id`
    * Description: Admins can remove a product from the catalog.

**Cart Management:**

* **View User Cart:**
    * Endpoint: `GET /cart/view`
    * Description: Users can view their shopping cart contents. (Requires User Authentication)
* **Add to Cart:**
    * Endpoint: `POST /cart/create/:productId`
    * Description: Users can add products to their shopping cart. (Requires User Authentication)
    * Body:
        * `productId`: Product's ID (required)
* **Increase Quantity:**
    * Endpoint: `PATCH /cart/increase/:userId/:productId`
    * Description: Users can increase the quantity of a specific item in their cart. (Requires User Authentication)
    * Body:
        * `userId`: User's ID (required)
        * `productId`: Product's ID (required)
* **Decrease Quantity:**
    * Endpoint: `PATCH /cart/decrease/:userId/:productId`
    * Description: Users can decrease the quantity of a specific item in their cart. (Requires User Authentication)
    * Body:
        * `userId`: User's ID (required)
        * `productId`: Product's ID (required)
* **Remove Cart Item:**
    * Endpoint: `DELETE /cart/delete/:userId/:productId`
    * Description: Users can remove items from their shopping cart. (Requires User Authentication)
    * Body:
        * `userId`: User's ID (required)
        * `productId`: Product'

**Order Management:**

* **Create Order:**
    * Endpoint: `POST /order/createOrder`
    * Description: Users can create orders for items in their cart. (Requires User Authentication)
* **View User Orders:**
    * Endpoint: `GET /order/users/:userId`
    * Description: Users can view all their orders. (Requires User Authentication)
    * Path Parameter:
        * `userId`: User's ID (required)
* **View All Orders (Admin Only):**
    * Endpoint: `GET /order/`
    * Description: Admins can view all user orders. (Requires Admin Authentication)
* **Get Single Order (Admin Only):**
    * Endpoint: `GET /order/:id`
    * Description: Admins can view details of a specific order. (Requires Admin Authentication)
    * Path Parameter:
        * `id`: Order ID (required)
* **Update Order Status (Admin Only):**
    * Endpoint: 
        * `PATCH /order/:id` (For Admins to update order status)
        * `PATCH /order/user/:id` (For Users to cancel their orders)
    * Description: Admins can update order status and users can cancel their orders.
    * Path Parameter:
        * `id`: Order ID (required)

**Admin Authentication:**

* **Register Admin:**
    * Endpoint: `POST /admin/register`
    * Description: Registers a new admin user.
    * Body:
        * `email`: Admin's email address (required)
        * `password`: Admin's password (required)
        * `fullName`: Admin's full name (required)
* **Login Admin:**
    * Endpoint: `POST /admin/login`
    * Description: Logs in an existing admin user.
    * Body:
        * `email`: Admin's email address (required)
        * `password`: Admin's password (required)
* **Logout Admin:**
    * Endpoint: `GET /admin/logout`
    * Description: Logs out the authenticated admin user. (Requires Admin Authentication)
* **View All Users (Admin Only):**
    * Endpoint: `GET /admin/view-users`
    * Description: Admins can view a list of all registered users. (Requires Admin Authentication)
* **Toggle User Suspension (Admin Only):**
    * Endpoint: `PATCH /admin/suspend-user/:userId`
    * Description: Admins can suspend or unsuspend user accounts. (Requires Admin Authentication)
    * Path Parameter:
        * `userId`: User ID (required)

**Getting Started:**

Follow these steps to set up and run the Spice Safari backend on your local machine:

**Prerequisites:**

* Node.js installed
* MongoDB installed and running

**Installation:**

1. Clone the repository:

```bash
git clone https://github.com/your-username/spice-safari-backend.git
```

2. Navigate to the project directory:

```bash
cd spice-safari-backend
```

3. Install dependencies:

```bash
npm install
```

4. Set up environment variables:

    Create a `.env` file in the root directory and define the following variables:

    ```
    # Database configuration
    DB_URL=your-connection-string

    # JWT secret key
    JWT_SECRET=your-secret-key

    # Others
    NODE_ENV=development
    PORT=4000
    ```

    Replace `your-secret-key` with a secure key for JWT authentication.

5. Run the server:

```bash
npm start
```

The backend should be running at http://localhost:4000.

**Contributing:**

Contributions to this project are welcome! Feel free to submit issues and pull requests.


