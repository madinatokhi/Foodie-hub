 🍔 Foodie Hub – Backend for Public Food Ordering System

 📌 Project Purpose
Foodie Hub is a public-facing food ordering platform that allows users to:
- Browse restaurants and menus
- Submit orders without needing to register
- View and manage customer info
- Track order statuses and history

This backend system is built using **Node.js**, **Express**, and **PostgreSQL**, and adheres to RESTful principles with a modular MVC architecture.

---

 🚀 Tech Stack
- Node.js
- Express.js
- PostgreSQL
- `pg` package (no ORM used)
- REST API
- Environment-based config

---

 🛠️ Setup Instructions

 1. Clone the repository
```bash
git clone https://github.com/madinatokhi/foodie-hub-backend.git
cd foodie-hub-backend
```

 2. Install dependencies
```bash
npm install
```

 3. Set up your environment variables

Create a `.env` file based on the example:

```bash
cp .env.example .env
```

Edit `.env` and set your database connection string:

```
DATABASE_URL=postgresql://<username>:<password>@localhost:5432/foodiehub
PORT=3000

```

 4. Initialize the database

Run the SQL script to create tables:

```bash
psql -U your_user -d foodiehub -f schema.sql
```

(Replace `your_user` with your PostgreSQL user.)

 5. Start the server

```bash
npm start
```

Server will run on:  
`http://localhost:3000`

---

 🧱 Database Design

Tables:
- `restaurants` – stores name, location, phone
- `menu_items` – linked to restaurant, stores name, price, availability
- `customers` – name and phone only
- `orders` – links customer and restaurant, tracks status
- `order_items` – junction table linking orders to menu items

Diagram: See `EER_Diagram.png` (submitted alongside this project)

---

 🔌 API Endpoints

 📍 Restaurants
| Method | Endpoint             | Description               |
|--------|----------------------|---------------------------|
| GET    | `/restaurants`       | List all restaurants      |
| POST   | `/restaurants`       | Create a restaurant       |
| PUT    | `/restaurants/:id`   | Update a restaurant       |
| DELETE | `/restaurants/:id`   | Delete a restaurant       |

---

 🍽️ Menu Items
| Method | Endpoint                         | Description                     |
|--------|----------------------------------|---------------------------------|
| GET    | `/menu/:restaurantId`            | List menu for restaurant        |
| POST   | `/menu/:restaurantId`            | Add menu item to restaurant     |
| PUT    | `/menu/:itemId`                  | Update a menu item              |
| DELETE | `/menu/:itemId`                  | Remove a menu item              |
| PATCH  | `/menu/:itemId/availability`     | Toggle item availability        |

---

 👤 Customers
| Method | Endpoint         | Description         |
|--------|------------------|---------------------|
| GET    | `/customers`     | List all customers  |
| POST   | `/customers`     | Add a new customer  |
| PUT    | `/customers/:id` | Update customer     |
| DELETE | `/customers/:id` | Delete customer     |

---

 🛒 Orders
| Method | Endpoint                      | Description                          |
|--------|-------------------------------|--------------------------------------|
| GET    | `/orders`                     | List all orders                      |
| GET    | `/orders?status=pending`      | Filter orders by status              |
| GET    | `/orders/customer/:id`        | Orders by customer ID                |
| GET    | `/orders/restaurant/:id`      | Orders by restaurant ID              |
| POST   | `/orders`                     | Place a new order                    |
| PUT    | `/orders/:id/status`          | Update order status                  |
| DELETE | `/orders/:id`                 | Cancel an order                      |

---

 ⭐ Bonus Endpoints
| Method | Endpoint                     | Description                        |
|--------|------------------------------|------------------------------------|
| GET    | `/orders/popular-menu-items` | Returns top-selling menu items     |

---

 🔍 Example: Placing an Order (POST `/orders`)
```json
{
  "customer_id": 2,
  "restaurant_id": 1,
  "status": "pending",
  "items": [
    { "menu_item_id": 3, "quantity": 2 },
    { "menu_item_id": 5, "quantity": 1 }
  ]
}
```

---

 📄 Submission Checklist

- [x] EER Diagram submitted
- [x] `schema.sql` ready
- [x] Backend implemented with Node.js + Express + pg
- [x] `.env.example` provided
- [x] Postman tested and working
- [x] `README.md` complete ✅

---

 🙌 Author
Built with 💻 by Madina Tokhi  
Student Assignment – Backend Development (Assignment 6)  
