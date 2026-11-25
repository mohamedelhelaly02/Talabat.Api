# Talabat.Api

E-commerce REST API built with ASP.NET Core (.NET 8). It covers user accounts, a product catalog, a basket, orders and Stripe payments.

## Features

- Accounts: register, login, current user, get and update the user's address, check if an email exists. JWT bearer authentication with ASP.NET Core Identity.
- Products: paginated list with filtering and sorting parameters, product by id, brands and types.
- Basket: get, create or update, delete, add item, update item quantity, remove item. Stored in Redis.
- Orders: create an order and list the signed-in user's orders (endpoints require authorization).
- Payments: Stripe payment intents, confirm payment intent, create payment method, and a Stripe webhook endpoint.
- Response caching with a Redis-backed cache service.
- Exception handling middleware and consistent error responses.
- Swagger UI in the Development environment.

## Architecture

Layered solution with four projects:

- `Talabat.Api`: controllers, DTOs, AutoMapper profile, middleware, extensions
- `Talabat.Core`: entities, specifications, repository and service interfaces
- `Talabat.Repository`: EF Core `StoreContext`, Identity context, generic repository, Unit of Work, basket repository, database seeding
- `Talabat.Service`: token, order, payment and cache services

Patterns used: Repository, Unit of Work, Specification, DTO mapping with AutoMapper.

## Tech stack

C#, ASP.NET Core 8, Entity Framework Core 8 (SQL Server), ASP.NET Core Identity, JWT, Redis (StackExchange.Redis), Stripe.net, AutoMapper, Swagger (Swashbuckle)

## Getting started

Requirements: .NET 8 SDK, SQL Server, Redis, a Stripe account.

1. Clone the repository

   ```sh
   git clone https://github.com/mohamedelhelaly02/Talabat.Api.git
   cd Talabat.Api
   ```

2. Set your own values in `Talabat.Api/appsettings.json` or with user secrets: `ConnectionStrings` (`DefaultConnection`, `IdentityConnection`, `RedisConnection`), `JWT` settings and `StripeKeys`.
3. Run the API. Migrations and seed data are applied automatically on startup.

   ```sh
   dotnet run --project Talabat.Api
   ```

4. Open Swagger at `/swagger` (Development environment).
