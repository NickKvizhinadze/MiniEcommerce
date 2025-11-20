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

## 3. High-Level Architecture

