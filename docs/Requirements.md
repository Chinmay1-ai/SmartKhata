# SmartKhata – Requirements

## 1. Project Overview

SmartKhata is a Digital Credit Ledger System designed for small businesses such as kirana stores, medical shops, stationery stores, and other local businesses.

The system helps shop owners digitally manage customer credit, payments, outstanding balances, transaction history, and reports instead of relying on traditional paper-based credit notebooks.

---

## 2. Problem Statement

Many small businesses still maintain customer credit records manually in notebooks.

This can lead to:

- Loss of records
- Manual calculation errors
- Difficulty finding old transactions
- Difficulty tracking outstanding balances
- No proper payment history
- No digital reports or analytics

SmartKhata aims to provide a simple and secure digital solution for managing customer credit and payment records.

---

## 3. Objectives

The main objectives of SmartKhata are:

- Digitize customer credit records.
- Maintain a complete customer transaction history.
- Automatically calculate outstanding balances.
- Provide secure Owner and Staff access.
- Provide search, filtering, pagination, and sorting.
- Generate customer statements and business reports.
- Provide dashboard analytics for shop owners.

---

## 4. Target Users

SmartKhata is primarily designed for:

- Kirana Stores
- Medical Shops
- Grocery Stores
- Stationery Shops
- Hardware Shops
- Small Retail Businesses
- Local Wholesalers

---

## 5. User Roles

### Owner

The Owner has complete access to the shop.

The Owner can:

- Manage shop profile.
- Manage staff.
- Manage customers.
- Add credit transactions.
- Record payments.
- View customer ledgers.
- View dashboard and analytics.
- Generate reports.
- View staff activity.

### Staff

Staff members have limited access.

Staff can:

- Login.
- View customers.
- Add customers.
- Update customer information.
- Add credit transactions.
- Record payments.
- View customer ledgers.
- View transaction history.

Staff cannot:

- Manage other staff members.
- Modify shop settings.
- Access Owner-only reports and management features.

---

# 6. Functional Requirements

Functional requirements define what the SmartKhata system should do.

## 6.1 Authentication

The system shall:

- Allow an Owner to register a new shop and Owner account.
- Allow users to login using email and password.
- Generate JWT access tokens after successful authentication.
- Generate refresh tokens.
- Allow users to refresh an expired access token using a valid refresh token.
- Allow authenticated users to logout.
- Allow authenticated users to change their password.
- Encrypt passwords using BCrypt.

---

## 6.2 Shop Management

The system shall:

- Allow authenticated users to view their shop profile.
- Allow the Owner to update shop information.
- Store shop name, address, contact number, and optional GST number.
- Use shop information in generated reports.

---

## 6.3 Staff Management

The system shall allow the Owner to:

- Add staff members.
- View staff members.
- View individual staff details.
- Update staff information.
- Activate or deactivate staff accounts.
- View staff activity.
- Prevent unauthorized staff-management operations.

---

## 6.4 Customer Management

The system shall allow Owner and Staff to:

- Add customers.
- View customer details.
- Update customer information.
- Search customers by name or phone number.
- Filter customers.
- Sort customer records.
- View customers using pagination.
- Activate or deactivate customers.
- View the customer's current outstanding balance.

Customer information shall include:

- Name
- Phone number
- Address
- Notes
- Status
- Created date
- Current balance

---

## 6.5 Transaction Management

The system shall support:

### Credit Transaction

A credit transaction represents goods or services provided to a customer on credit.

The system shall:

- Allow Owner and Staff to create credit transactions.
- Store customer, amount, description, payment method, date, and creator.
- Update the customer's outstanding balance.

### Payment Transaction

A payment transaction represents money received from a customer.

The system shall:

- Allow Owner and Staff to record customer payments.
- Store customer, amount, payment method, description, date, and creator.
- Reduce the customer's outstanding balance.

---

## 6.6 Digital Ledger

The system shall maintain a digital ledger for every customer.

The ledger shall display:

- Transaction date
- Transaction type
- Description
- Credit amount
- Payment amount
- Balance after transaction
- User who created the transaction

The system shall automatically calculate the customer's outstanding balance.

---

## 6.7 Transaction Search and Filtering

The system shall allow transactions to be:

- Filtered by date range.
- Filtered by transaction type.
- Filtered by payment method.
- Filtered by customer.
- Sorted by date.
- Displayed using pagination.

---

## 6.8 Transaction Integrity

The system shall protect financial transaction history.

- Transaction amounts should not be freely modified after creation.
- Financial transactions should not be physically deleted.
- Transaction reversal should be used where required.
- Transaction operations should be executed within appropriate database transactions.
- Failed operations should be rolled back.

---

## 6.9 Dashboard and Analytics

The system shall provide dashboard information including:

- Today's credit.
- Today's collection.
- Total outstanding amount.
- Total customers.
- Active customers.
- Recent transactions.
- Monthly credit and collection trends.
- Top customers by outstanding balance.
- Overdue customers.

---

## 6.10 Overdue Customers

The system shall identify customers who have outstanding balances for a defined period.

The system should support overdue categories such as:

- 30 days
- 60 days
- 90 days

---

## 6.11 Reports

The system shall provide:

### PDF

- Customer statement.
- Customer transaction history.
- Outstanding balance.
- Shop information.

### Excel

- Customer list.
- Transaction records.
- Outstanding customer report.

---

## 6.12 API Documentation

The system shall provide API documentation using Swagger/OpenAPI.

The documentation should include:

- Available APIs.
- Request parameters.
- Request bodies.
- Response structures.
- Authentication requirements.

---

# 7. Non-Functional Requirements

## 7.1 Security

- Authentication shall use JWT.
- Passwords shall be encrypted using BCrypt.
- APIs shall use role-based authorization.
- Users shall only access data belonging to their own shop.
- `shopId` shall be derived from authenticated user context rather than trusted from client requests.
- Owner-only APIs shall not be accessible to Staff.

---

## 7.2 Performance

- Large customer and transaction lists shall use pagination.
- Database queries should retrieve only required data.
- Appropriate indexes should be used for frequently searched fields.
- Hibernate fetching strategies should be selected appropriately.

---

## 7.3 Reliability

- Financial operations shall maintain database consistency.
- Failed transaction operations shall be rolled back.
- The system should prevent duplicate or inconsistent transaction records.

---

## 7.4 Maintainability

The backend shall follow layered architecture:

Controller → Service → Repository → Database

The application shall use:

- DTOs
- Proper exception handling
- Validation
- Clear package structure
- Meaningful naming conventions

---

## 7.5 Scalability

The application architecture should allow future features such as:

- Multiple shop branches
- Notifications
- WhatsApp/SMS reminders
- UPI integration
- Mobile application

without requiring major changes to the existing architecture.

---

## 7.6 Usability

Common operations should require minimal steps.

For example:

Customer → Credit/Payment → Amount → Save

The interface should provide clear information about:

- Outstanding balance
- Transaction history
- Payment status
- Customer details

---

# 8. V1 Scope

The first version of SmartKhata will include:

- Authentication
- JWT and Refresh Token
- Shop Management
- Staff Management
- Customer Management
- Credit Transactions
- Payment Transactions
- Digital Ledger
- Search
- Filtering
- Pagination
- Sorting
- Dashboard
- Analytics
- Overdue Customers
- PDF Statements
- Excel Reports
- Swagger/OpenAPI
- Bean Validation
- Global Exception Handling
- Audit Logging
- Hibernate/JPA Relationships

---

# 9. Future Scope

The following features are planned for future versions:

- SMS reminders
- WhatsApp reminders
- Email notifications
- UPI integration
- QR-based payments
- GST invoice generation
- Mobile application
- Multi-branch support
- Redis caching
- Docker
- CI/CD
- Advanced analytics
