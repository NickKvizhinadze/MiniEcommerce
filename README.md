# Mini Ecommerce Web API  
A small, beginner-friendly Web API project using ASP.NET Core + SQLite.  
Built to teach real backend concepts including database access, migrations, CRUD patterns, and clean layering.

---

## 0. Project Setup Tasks (Before Coding)

### Create the Project (Visual Studio)
1. Create a new solution named **MiniEcommerce**.
2. Add a new **ASP.NET Core Web API** project named `MiniEcommerce.Api`.
3. Use `.NET 8` or the latest LTS version.
4. Ensure "Use Controllers" is enabled.
5. Run the project once to confirm it starts successfully.

### Project Structure
Inside `MiniEcommerce.Api`, create folders:
- `Controllers`
- `Models`
- `Data`
- `Services`

### Configure SQLite
1. Add a SQLite connection string in `appsettings.json`.  
2. Install EF Core packages for SQLite:
   - `Microsoft.EntityFrameworkCore`
   - `Microsoft.EntityFrameworkCore.Sqlite`
   - `Microsoft.EntityFrameworkCore.Tools`
3. Create a `MiniEcommerceDbContext` class.
4. Register the DbContext inside DI (Dependency Injection).
5. Run the first EF Core migration and create the SQLite database.

At this point, the API has a real persistent database powering it.

---

## 1. Project Overview

The Mini Ecommerce API simulates a tiny online shop.  
Users can browse products, manage a cart, and place orders.  
Data is stored in a simple SQLite database to teach CRUD operations and migrations.

---

## 2. System Features

### Product Catalog API
- Fetch all products  
- Fetch product by ID  

### Shopping Cart API
- Add a product to cart  
- Remove product from cart  
- View cart contents  
- Calculate cart total  

### Order API
- Create an order from the cart  
- View order details  

SQLite makes the experience feel like working with a real backend system.

---

## 3. System Diagram (Conceptual)

```
+-------------+       adds/removes        +----------------+
|   Client    | ------------------------> |  Shopping Cart |
+-------------+                            +----------------+
      |                                                |
      | browses products                               | converts to
      v                                                v
+-------------+        places orders           +----------------+
|  Products   | -----------------------------> |    Orders     |
+-------------+                                +----------------+
```

---

## 4. Project Milestones

The project is divided into clear, practical milestones.

---

## Milestone 1 — Product Management

### Purpose
Enable the API to hold and serve product data.

### Tasks
- Create `Product` entity with fields:
  - Id
  - Name
  - Description
  - Price
  - StockQuantity
- Create `ProductDto` for create/update requests.
- Add `ProductsController` with CRUD endpoints:
  - Create product
  - Edit product
  - Delete product
  - Get product by id
  - Get all products (with optional search filter)
- Implement product validation (name length, positive price, quantity ≥ 0).
- Add seed data via `OnModelCreating`.

**Deliverable:** Fully working product catalog.

---

## Milestone 2 — User Management

### Purpose
Add minimal user/customer handling.

### Tasks
- Create `User` entity with:
  - Id
  - FullName
  - Email
- Create CRUD endpoints in `UsersController`.
- Basic validation (valid email format).
- No authentication required — keep it simple.

**Deliverable:** Users can be created and used in orders.

---

## Milestone 3 — Shopping Cart

### Purpose
Simulate a very simple cart per user.

### Requirements
- One shopping cart per user.
- A cart holds multiple items.
- An item references:
  - ProductId
  - Quantity

### Tasks
- Create entities:
  - `Cart`
  - `CartItem`
- Implement endpoints in `CartController`:
  - Add product to cart
  - Remove product from cart
  - Change quantity
  - View cart
  - Empty cart
- Validate:
  - Quantity > 0
  - Product stock ≥ requested

**Deliverable:** Functional shopping cart with validations.

---

## Milestone 4 — Orders & Checkout

### Purpose
Convert the shopping cart into an order.

### Tasks
- Create `Order` and `OrderItem` entities.
- Add endpoints in `OrdersController`:
  - Create order from cart
  - View user’s orders
  - Get order by id
- On checkout:
  - Validate enough stock
  - Deduct product stock
  - Save order
  - Empty cart

**Deliverable:** End-to-end e‑commerce ordering pipeline.

---

## Milestone 5 — Database & Persistence

### Purpose
Switch everything from theory to a real SQLite database.

### Tasks
- Run `Add-Migration InitialCreate`
- Run `Update-Database`
- Confirm that `ecommerce.db` is created in the project root.
- Test all CRUD endpoints via Swagger.

**Deliverable:** Fully persistent mini‑ecommerce API.

---

## Milestone 6 — Documentation & Cleanup

### Purpose
Prepare the project for sharing or teaching.

### Tasks
- Add XML documentation comments.
- Organize folder structure.
- Add a final architecture diagram:

```
Controllers → Services → EF Core → SQLite
```

- Include sample request/response examples in the README.
- Comment code clearly for beginners.

**Deliverable:** Clean, documented project ready for your friend to learn from.

---

## Next Steps (Optional Features)

If your friend enjoys the project, consider adding:
- Pagination
- Sorting & filtering
- Simple JWT authentication
- Product categories
- Discount codes
- Admin panel (later web UI)

These push the project closer to real e‑commerce architecture.

---

## End
This README serves as a project blueprint — a roadmap from empty solution to a functioning API. It’s perfect for a beginner who learns by building.

Happy coding!
