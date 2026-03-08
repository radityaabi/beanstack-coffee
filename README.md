# Beanstack Coffee ☕

[Beanstack Coffee](https://beanstackcoffee.radityaabi.com) Simple Ecommerce Platform for Specialty Coffee Beans

Beanstack Coffee is a modern, lightweight ecommerce application designed to showcase and sell unique specialty coffee beans.
This project is built as a portfolio-grade fullstack application, focusing on clean architecture, RESTful API design, and real-world ecommerce flows such as product catalog, shopping cart, checkout, and order management.

Live Demo: https://beanstackcoffee.radityaabi.com

## Links

- Website/Frontend: <https://beanstackcoffee.radityaabi.com>
  - Backend API: <https://beanstackcoffee-api.radityaabi.com>
- Repositories:
  - General: <https://github.com/radityaabi/beanstackcoffee>
  - Backend API: <https://github.com/radityaabi/beanstackcoffee-api>
  - Frontend Web: <https://github.com/radityaabi/beanstackcoffee-web>
- Project Management: <https://linear.app/beanstackcoffee>

Inspirations:

- <https://ottencoffee.co.id> - Otten Coffee is an Indonesian ecommerce platform dedicated to coffee lovers.
- <https://shop.toffin.id/> - Toffin Digital E-Commerce is an online platform by Toffin Indonesia, offering integrated solutions for coffee and beverage businesses.

## Features

- Home page
  - Hero section
  - Products catalogue. Example: <https://beanstackcoffee.radityaabi.com/products>
- Product page
  - Image URL
  - SKU (stock keeping unit)
  - Name
  - Price
  - Description
  - Stock level / In stock or not
  - Add to Cart Form:
    - Quantity Input
    - Increment & Decrement Button
    - Add to Cart Submit Button
- Shopping Cart page
  - Product items to buy
    - Image, name, price, quantity, subtotal (price x quantity)
    - Remove item
    - Change quantity form
  - Link: continue shopping, go to products catalogue
  - Link: checkout
- Checkout page
  - Order summary
    - Product items to buy
    - Grand total of all product items to buy
- Place order / transaction is being processed

## UI Designs

- Figma: <https://www.figma.com/design/x1LomxF9N55tv0VMqg4KwK/Beanstack-Coffee?t=Fsjc2GnCvTfESuzZ-1>

## Backend REST API Endpoints

- Production: `https://beanstackcoffee-api.radityaabi.com`
- Local: `http://localhost:3000`

Priority:

| Endpoint           | HTTP  | Description         | Permission |
| ------------------ | ----- | ------------------- | ---------- |
| `/products`        | `GET` | Get all products    | Public     |
| `/products/{slug}` | `GET` | Get product by slug | Public     |

With Auth:

| Endpoint         | HTTP   | Description              | Permission    |
| ---------------- | ------ | ------------------------ | ------------- |
| `/users`         | `GET`  | Get all users            | Public        |
| `/users/{id}`    | `GET`  | Get user by id           | Public        |
| `/auth/register` | `POST` | Register new user        | Public        |
| `/auth/login`    | `POST` | Login user               | Public        |
| `/auth/me`       | `GET`  | Check authenticated user | Authenticated |
| `/auth/logout`   | `POST` | Logout user              | Authenticated |

Cart:

| Endpoint           | HTTP     | Description                    | Permission    |
| ------------------ | -------- | ------------------------------ | ------------- |
| `/cart`            | `GET`    | Get user's cart                | Authenticated |
| `/cart/items`      | `PUT`    | Add product & quantity to cart | Authenticated |
| `/cart/items/{id}` | `DELETE` | Delete product from cart       | Authenticated |
| `/cart/items/{id}` | `PATCH`  | Update product quantity        | Authenticated |

## Frontend Pages

Priority:

| Route             | Title                    |
| ----------------- | ------------------------ |
| `/`               | Home Page                |
| `/products`       | All Products Page        |
| `/products/:slug` | One Product by Slug Page |

With Auth:

| Route        | Title                   | Permission    |
| ------------ | ----------------------- | ------------- |
| `/register`  | Register Page           | Public        |
| `/login`     | Login Page              | Public        |
| `/dashboard` | Authenticated User Page | Authenticated |
| `/logout`    | Logout Page             | Authenticated |
| `/cart`      | Cart Page               | Authenticated |

## Data Structure

### Product

```json
{
  "id": "ULID123",
  "slug": "mens-rea-blend-340g",
  "name": "Mens Rea Blend 340g",
  "sku": "CF-BEANS-1",
  "weight": 340,
  "price": 149000,
  "stockQuantity": 10,
  "imageUrl": "https://uploadcare.com/images/image.jpg",
  "description": "...",
  "createdAt": "...",
  "updatedAt": "..."
}
```

### Add New Product

Request Body:

```json
{
  "name": "Mens Rea Blend 340g",
  "price": 149000,
  "sku": "CF-BEANS-1",
  "weight": 340,
  "stockQuantity": 10,
  "imageUrl": "https://uploadcare.com/images/image.jpg",
  "description": "..."
}
```

Response Body:

```json
{
  "id": "ULID234",
  "slug": "mens-rea-blend-340g",
  "name": "Mens Rea Blend 340g",
  "weight": 340,
  "price": 149000,
  "sku": "CF-BEANS-1",
  "stockQuantity": 10,
  "imageUrl": "https://uploadcare.com/images/image.jpg",
  "description": "..."
}
```