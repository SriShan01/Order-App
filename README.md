# Order Management App

A minimal full-stack application for managing users, products, and orders. Built with **NestJS**, **Prisma**, **PostgreSQL**, **Redis**, **Next.js**, and **TailwindCSS**.

---

## **Project Structure**

- **Backend**: NestJS + Prisma + PostgreSQL + Redis  
  Github repo - https://github.com/SriShan01/backend
  `http://localhost:4000` (default local port)

- **Frontend**: Next.js + TailwindCSS  
  Github repo - https://github.com/SriShan01/frontend
  `http://localhost:3000` (default local port)

---

## **Prerequisites**

Make sure the following are installed on your machine:

- Node.js (latest LTS)
- npm or yarn
- PostgreSQL (running)
- Redis (running)

---

## **Backend Setup (NestJS)**

1. Navigate to the backend folder:
cd backend

Install dependencies:

npm install
Create a .env file in the backend root:
DATABASE_URL="postgresql://postgres:<password>@localhost:5432/assessment_db?schema=public"
REDIS_URL="redis://localhost:6379"
Replace <password> with your PostgreSQL password. Make sure PostgreSQL and Redis are running.

Run Prisma migrations:
npx prisma migrate dev --name init

Start the backend server:
npm run start:dev
The backend will run at http://localhost:4000.

Frontend Setup (Next.js + TailwindCSS)

Navigate to the frontend folder:
cd frontend

Install dependencies:
npm install

Start the frontend server:
npm run dev

The frontend will run at http://localhost:3000.

Navigate to http://localhost:3000/orders

Features

Create Orders (transactionally)

Please create test product and test user in the sql end using sql queries. This way we can specify user id and product id:

INSERT INTO "User" (name, email) 
VALUES ('Test User', 'testuser@example.com');

-- Create a test product
INSERT INTO "Product" (name, price) 
VALUES ('Test Product', 99.99);

List Orders with optional search

Redis caching for orders (30-second TTL)

Mock async order confirmation

Responsive UI with TailwindCSS

Developer Experience (DX)
Trade-offs / Shortcuts:

No authentication implemented to keep the project minimal.

Mock async order confirmation via setTimeout instead of a real queue.

Minimal input validation; assumes valid numeric IDs for simplicity.

Single-page management of Users, Products, and Orders for convenience.

Redis cache invalidation only happens on order creation; updates to users/products do not affect cache.

Environment requirements:

PostgreSQL must be running locally with a database named assessment_db.

Redis must be running locally for caching orders.

Optional Improvements for Production:

Add authentication and authorization.

Implement proper queue system (SQS, BullMQ) for async order confirmation.

Add pagination metadata in GET /orders.

Links
Frontend: http://localhost:3000

Backend: http://localhost:4000

