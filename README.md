# Merce Italiana — Private-Code Case Study

> **Public case study for a private project.** The application's source repository is private. This repository contains project information and approved screenshots only; it does not contain application source code, credentials, or internal configuration.

## Project overview

Merce Italiana is a full-stack retail management platform for a clothing store. Its scope brings together product and inventory management, customer and order workflows, staff access, reporting, and a separate customer-facing storefront.

## My role

This is my full-stack project. I work across the Java/Spring Boot backend and React-based web applications, connecting business workflows to REST APIs and relational persistence.

## How it works

The staff application and customer storefront are separate React/Vite frontends that communicate with a Spring Boot REST API. The backend uses permission-aware endpoints and data-transfer objects, while PostgreSQL schema changes are managed through Flyway migrations. H2 is used for local/test scenarios.

## Main capabilities

- Product catalog and inventory workflows
- Customer, cart, and order management
- Staff roles and permission-controlled access
- Operational dashboards, reports, and notifications
- Cash-based payment status handling
- Separate customer storefront and staff application

## Technology and tools

- **Languages:** Java, JavaScript, SQL, HTML, CSS
- **Backend:** Spring Boot, Spring Security, Spring Data JPA, REST APIs, WebSocket
- **Frontend:** React, Vite, Tailwind CSS, Axios, TanStack Query
- **Data and migrations:** PostgreSQL, H2, Flyway
- **Authentication and access:** JWT, roles and permissions
- **Build and delivery:** Maven Wrapper, npm, Git, automated tests

## Engineering approach

The project uses separate customer and staff interfaces over a shared API. Backend DTOs define API responses, authorization is checked by role and permission, and Flyway migrations track schema changes. The order lifecycle includes inventory updates and audited payment-status changes.

## Current status

This is an active development project. Production deployment configuration and full test verification remain in progress; some test failures need to be resolved before a production release.

## Screenshots

Screenshots will be added in a later update using synthetic or anonymized data.

## Source code and confidentiality

The original source repository is private. This public case study describes the project at a high level and excludes source files, credentials, local machine paths, private deployment details, and real customer or business data.
