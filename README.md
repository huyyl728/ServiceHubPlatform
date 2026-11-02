# ServiceHubPlatform

A scalable multi-service booking and marketplace platform built with ASP.NET Core 10, C#, and a Modular Monolith architecture.

## About the Project

ServiceHubPlatform aims to connect customers with local service providers through a unified platform.

The platform is designed to support restaurants, sports facilities, salons, spas, and other everyday services.

This project is being developed from scratch as a long-term software engineering and portfolio project.

## Technology Stack

- Backend: ASP.NET Core 10 MVC, C#
- Database (planned): PostgreSQL
- ORM (planned): Entity Framework Core
- Architecture: Modular Monolith
- Frontend: Razor Views, HTML, CSS, JavaScript
- Version Control: Git and GitHub
- DevOps (planned): Docker, CI/CD
- Testing (planned): Unit and Integration Tests

## Project Architecture

ServiceHubPlatform is organized into four projects:

- ServiceHub.Web: MVC controllers, views, and web configuration.
- ServiceHub.Application: Application services, use cases, DTOs, and interfaces.
- ServiceHub.Domain: Domain entities and business rules.
- ServiceHub.Infrastructure: Database access and external integrations.

The goal is to keep business logic independent of presentation and infrastructure concerns.

## Planned Features

- User authentication and role-based authorization
- Business and service management
- Smart service search and suggestions
- Restaurant and service discovery
- Appointment and table reservations
- Membership programs and exclusive offers
- Vouchers and promotions
- Food ordering and delivery
- Payments and transaction history
- Reviews and notifications
- Administrative dashboards

## Getting Started

### Requirements

- .NET SDK 10
- Git

### Build the Solution

```bash
dotnet restore ServiceHubPlatform.sln
dotnet build ServiceHubPlatform.sln
```

### Run the Website

```bash
dotnet run --project src/ServiceHub.Web/ServiceHub.Web.csproj
```

Open the localhost URL displayed in the terminal.

## Development Roadmap

1. Project Initialization and GitHub
2. Architecture and Database Design
3. UI and Design System
4. Authentication and Authorization
5. Business and Service Management
6. Search and Discovery
7. Booking and Reservations
8. Promotions and Membership
9. Food Ordering and Delivery
10. Payments, Reviews, and Notifications
11. Dashboard, Security, and Optimization
12. Deployment and Portfolio

## Current Status

Phase 1 - Project Initialization (In Progress)

Completed:
- Git repository initialized
- .NET 10 Solution created
- Four projects created
- Project references configured
- Solution builds successfully
- Default MVC website runs locally

Database integration and business features are not implemented yet.

## Project Vision

Build a maintainable, testable, and extensible platform that can evolve into a production-ready multi-service ecosystem.
