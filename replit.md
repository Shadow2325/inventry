# Overview

This is a React-based inventory management system for electrical components, specifically designed for managing different types, sizes, and voltage levels of electrical equipment. The application provides a comprehensive dashboard for tracking stock levels, managing inventory items, and generating reports. It features a modern UI built with React and TypeScript, with a full-stack architecture using Express.js for the backend and PostgreSQL for data storage.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture

The frontend uses React with TypeScript and follows a component-based architecture with the following key decisions:

- **UI Framework**: Uses shadcn/ui components built on top of Radix UI primitives for consistent, accessible design
- **Styling**: Tailwind CSS with CSS custom properties for theming and responsive design
- **State Management**: React Query (TanStack Query) for server state management, with React hooks for local state
- **Routing**: Wouter for lightweight client-side routing
- **Form Handling**: React Hook Form with Zod for schema validation
- **Build Tool**: Vite for fast development and optimized production builds

The frontend is organized into logical directories:
- `pages/` - Route components for different application views
- `components/` - Reusable UI components organized by feature
- `hooks/` - Custom React hooks for data fetching and business logic
- `lib/` - Utility functions, API clients, and shared configurations

## Backend Architecture

The backend uses Express.js with TypeScript and follows a layered architecture:

- **Web Framework**: Express.js with middleware for JSON parsing, logging, and error handling
- **Database Layer**: Drizzle ORM for type-safe database operations with PostgreSQL
- **API Design**: RESTful API endpoints organized by resource type
- **Data Storage**: Storage abstraction layer to decouple business logic from database implementation
- **Development Setup**: Vite integration for hot module replacement in development

Key architectural patterns:
- Repository pattern through the storage interface for data access
- Middleware-based request processing pipeline
- Centralized error handling
- Type-safe schema definitions shared between frontend and backend

## Database Design

PostgreSQL database with Drizzle ORM providing:

- **Hierarchical Structure**: Voltage levels → Sizes → Types → Inventory items
- **Stock Tracking**: Inventory quantities with minimum threshold alerts
- **Audit Trail**: Stock movements table for tracking all inventory changes
- **User Management**: Basic user authentication and role-based access

The schema supports complex filtering and reporting while maintaining referential integrity through foreign key relationships.

## Component Structure

The application uses a hierarchical inventory classification system:
- **Voltage Levels** (e.g., 11kV, 22kV, 33kV)
- **Sizes** within voltage levels (e.g., 95 sqmm, 185 sqmm)
- **Types** within sizes (e.g., Indoor, Outdoor, Straight-through)
- **Inventory Items** for each type with quantity tracking

This structure allows for detailed categorization and efficient filtering of electrical components.

# External Dependencies

## Database Services
- **PostgreSQL**: Primary database for storing inventory data, user information, and stock movements
- **Neon Database**: Cloud PostgreSQL service integration via `@neondatabase/serverless`

## UI and Styling
- **Radix UI**: Comprehensive primitive components for building accessible interfaces
- **Tailwind CSS**: Utility-first CSS framework for rapid styling
- **Lucide React**: Icon library for consistent iconography

## Development and Build Tools
- **Vite**: Development server and build tool with fast HMR
- **TypeScript**: Static type checking across the entire application
- **Replit Integration**: Development environment plugins for enhanced debugging

## Form and Data Management
- **React Hook Form**: Performant form library with minimal re-renders
- **Zod**: Schema validation for type-safe data handling
- **TanStack Query**: Server state management with caching and synchronization
- **Drizzle ORM**: Type-safe database operations and migrations

## Authentication and Session Management
- **connect-pg-simple**: PostgreSQL session store for Express sessions
- **Express Session**: Server-side session management

The application is designed to be self-contained with minimal external service dependencies, making it suitable for deployment in various environments while maintaining data sovereignty.