# SmartKhata

### Digital Credit Ledger System

SmartKhata is a Digital Credit Ledger System designed for small businesses to digitally manage customer credit, payments, outstanding balances, and transaction history.

## Problem

Many small businesses still maintain customer credit records using traditional paper-based notebooks. This can lead to lost records, calculation errors, difficulty tracking payments, and lack of proper transaction history.

SmartKhata aims to digitize this process through a simple and secure web application.

## Key Features

- 🔐 JWT Authentication
- 👥 Owner & Staff Role-Based Access
- 🏪 Shop Management
- 👤 Customer Management
- 💰 Credit & Payment Transactions
- 📒 Digital Customer Ledger
- 🔍 Search, Filtering & Pagination
- 📊 Dashboard & Analytics
- ⚠️ Overdue Customer Tracking
- 📄 PDF Customer Statements
- 📊 Excel Reports
- 📖 Swagger/OpenAPI Documentation
- 🛡️ Bean Validation & Global Exception Handling
- 📝 Audit Logging

## Tech Stack

### Backend

- Java
- Spring Boot
- Spring Security
- JWT
- Hibernate
- Spring Data JPA
- MySQL
- Maven
- Swagger/OpenAPI

### Frontend

- React
- Tailwind CSS
- Axios
- React Router
- Chart.js / Recharts

## Architecture

```text
React Frontend
       ↓
REST APIs
       ↓
Spring Boot
       ↓
Spring Security + JWT
       ↓
Service Layer
       ↓
Spring Data JPA / Hibernate
       ↓
MySQL
