# Merce Italiana — Private-Code Case Study

> **Private project, public case study.** The application's source repository is private. This repository documents the product, architecture, workflows, and technologies at a non-sensitive level. No application source code, credentials, internal configuration, or real customer or business data is published here.

## At a glance

Merce Italiana is a clothing-retail platform with two connected experiences: a customer storefront and a staff application. Both use a shared backend for product, inventory, customer, and order workflows.

**My role:** Full-stack developer  
**Application shape:** React customer and staff apps → Spring Boot REST API → PostgreSQL  
**Project status:** Active development; production configuration and full test verification are still in progress.

## The problem it addresses

A clothing business needs to present products to customers while keeping its internal operations organized. Product availability, customer orders, staff access, and operational reporting are related, but each audience needs a different interface.

Merce Italiana separates the customer shopping experience from staff operations while connecting both to shared backend data and business workflows.

## People and access

- **Customers** use the storefront to browse the catalog, manage a cart, and place orders.
- **Staff members** use the staff application for product and inventory operations, customer and order workflows, and operational information.
- **Users with elevated permissions** access management and reporting capabilities allowed by their assigned roles and permissions.

JWT-based authentication and backend role/permission checks protect staff capabilities. The exact permission matrix and business-specific policies are private.

## End-to-end workflows

### Customer order flow

1. **Browse products.** A customer views the catalog in the React storefront.
2. **Build a cart.** The customer selects products and reviews the cart in the storefront.
3. **Submit an order.** The frontend sends the required request to the Spring Boot API. The backend validates the request and applies the order workflow.
4. **Track the order state.** The API returns order information that the client can display. Staff can access the corresponding order workflow in the staff application.
5. **Handle payment status.** The project includes cash-based payment status handling. The status is managed through backend workflows rather than treated as a completed online payment.
6. **Update inventory.** Order processing includes inventory updates so that stock data remains connected to order activity.
7. **Review operations.** Staff use operational views and reports to follow products, inventory, customers, orders, and notifications.

### Staff product and inventory flow

1. A staff member signs into the staff application.
2. The frontend requests data and actions from the REST API.
3. The backend authenticates the user and checks the relevant role and permission.
4. Authorized product or inventory changes are validated and persisted.
5. Updated information is returned to the staff interface and is available to related workflows.

These descriptions summarize the project at a high level. They do not publish private business rules, endpoint details, or real store data.

## System overview

```text
Customer ──► React storefront ──┐
                                │
Staff ─────► React staff app ───┼──► Spring Boot REST API
                                │     Security · roles/permissions
                                │     Orders · inventory · reporting
                                │            │
                                └────────────┘
                                             ▼
                              PostgreSQL · JPA · Flyway
                              H2 for local/test scenarios
```

The customer and staff applications are distinct frontends with different responsibilities. They share backend capabilities and persisted business data through the API. The backend uses data-transfer objects to define API-facing data and applies access checks to protected operations.

## Architecture and engineering

### Customer and staff frontends

Both frontends use React and Vite. Tailwind CSS supports styling. Axios handles API communication, while TanStack Query supports client-side retrieval and synchronization of server data.

### Backend services

The Java backend uses Spring Boot to provide REST APIs and application workflows. Spring Security handles protected access. Spring Data JPA connects workflows to relational persistence. WebSocket support is included for notification-related capabilities.

### Persistence and migrations

PostgreSQL is the primary relational database. Flyway migrations version schema changes. H2 supports local and test scenarios. This separation lets the application exercise database-backed workflows without publishing production data or configuration.

### Authentication and authorization

JWT supports authenticated requests. Backend roles and permissions govern access to staff operations. The authorization checks live in the server-side layer, which is the authoritative boundary for protected actions.

### Build, quality, and delivery

The backend uses the Maven Wrapper; frontend dependencies and scripts use npm. Git supports source control. Automated tests are part of the project, but full test verification remains in progress. Production deployment configuration is also not yet complete.

## My contribution

As the full-stack developer, I work across the React applications and Spring Boot API, connecting customer and staff workflows to shared business data. The project covers frontend integration, backend/API behavior, relational data and migrations, authentication and authorization, and testing.

## Technology

- **Languages:** Java, JavaScript, SQL, HTML, CSS
- **Frontend:** React, Vite, Tailwind CSS, Axios, TanStack Query
- **Backend:** Spring Boot, Spring Security, Spring Data JPA
- **API and live updates:** REST APIs, WebSocket
- **Authentication and access:** JWT, roles, permissions
- **Database:** PostgreSQL; H2 for local/test scenarios
- **Schema management:** Flyway
- **Build and collaboration:** Maven Wrapper, npm, Git, automated tests

## Current status

This is an active development project. Production deployment configuration and full test verification remain in progress, and some test failures still need to be resolved before a production release. This case study describes the current project scope; it does not claim a production-ready release.

## Screenshots

Screenshots will be added later. They will use synthetic or anonymized data and will be reviewed to avoid exposing private customer, order, or business information.

## Privacy boundary

The original source repository is private. This public case study is a product and engineering overview, not a copy of that repository. It excludes source files, secrets, private endpoints, deployment configuration, real customer records, and internal business data.
