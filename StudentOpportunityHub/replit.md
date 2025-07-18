# Gigzo - Student Opportunity Platform

## Overview

Gigzo is a visually rich, responsive, dark-themed website that connects college students with real-time paid gigs in events like college fests, expos, corporate events, and summits. The platform enables students to earn money, gain experience, and grow their skills while helping event organizers find qualified talent quickly.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework & Libraries:**
- **React 18** with TypeScript for the main UI framework
- **Vite** as the build tool and development server
- **Wouter** for client-side routing (lightweight React Router alternative)
- **TanStack Query (React Query)** for server state management and API calls
- **Framer Motion** for animations and page transitions
- **Tailwind CSS** with custom design system for styling

**UI Component System:**
- **Radix UI** primitives for accessible, unstyled components
- **shadcn/ui** component library built on top of Radix UI
- Custom theme with dark mode support using CSS variables
- Responsive design with mobile-first approach

**Design System:**
- Dark-themed with navy, charcoal, light blue, electric purple, and aqua colors
- Custom CSS variables for consistent theming
- Typography and spacing scales defined in Tailwind config
- Smooth animations and hover effects throughout

### Backend Architecture

**Server Framework:**
- **Express.js** with TypeScript for the REST API server
- **ESM modules** for modern JavaScript syntax
- Middleware for request logging, JSON parsing, and error handling

**Development Setup:**
- **tsx** for TypeScript execution in development
- **esbuild** for production builds
- Hot module replacement (HMR) via Vite integration
- Development and production environment configurations

### Data Storage Solutions

**Database:**
- **PostgreSQL** as the primary database (configured via DATABASE_URL)
- **Drizzle ORM** for type-safe database operations
- **Neon Database** serverless PostgreSQL provider (@neondatabase/serverless)
- **connect-pg-simple** for PostgreSQL session storage

**Schema Design:**
- Users table with id, username, and password fields
- Zod schemas for runtime validation
- Type inference from database schema to TypeScript types

**Development Storage:**
- In-memory storage implementation for development/testing
- Interface-based storage abstraction for easy swapping between implementations

## Key Components

### Frontend Components

**Page Structure:**
- **Navigation** - Fixed header with smooth scroll navigation
- **Hero Section** - Full-screen background with "EARN. LEARN. GROW." slogan
- **What We Do** - Feature overview with icons and descriptions
- **Why Us** - Benefits for students and organizers
- **How It Works** - Step-by-step process flows
- **CTA Section** - Call-to-action buttons for students and organizers
- **Testimonials** - User reviews and ratings
- **Trust Score** - Statistics and partner logos
- **Footer** - Links and contact information

**Interactive Features:**
- Intersection Observer hooks for scroll-triggered animations
- Counter animations for statistics
- Smooth scrolling navigation
- Mobile-responsive design with hamburger menu
- Hover effects and micro-interactions

### Backend Components

**API Structure:**
- RESTful endpoints with `/api` prefix
- Request/response logging middleware
- Error handling with proper HTTP status codes
- CORS and security headers

**Storage Interface:**
- Abstract storage interface for CRUD operations
- User management (create, get by ID, get by username)
- Extensible design for additional entities

## Data Flow

### Client-Server Communication

**API Layer:**
- Fetch-based HTTP client with credential support
- Centralized error handling and response parsing
- Query client configuration for caching and background updates

**State Management:**
- Server state managed by TanStack Query
- Local component state for UI interactions
- Form state with React Hook Form and Zod validation

**Authentication Flow:**
- Session-based authentication (ready for implementation)
- Cookie-based session storage
- Unauthorized request handling

### Database Operations

**ORM Integration:**
- Drizzle ORM for type-safe queries
- Schema-first approach with TypeScript inference
- Migration support via drizzle-kit

**Data Validation:**
- Zod schemas for runtime type checking
- Input validation on both client and server
- Type-safe API contracts

## External Dependencies

### Frontend Dependencies

**Core Libraries:**
- React ecosystem (React 18, React DOM, React Query)
- Routing and state management (Wouter, TanStack Query)
- Styling and animations (Tailwind CSS, Framer Motion)
- Form handling (React Hook Form, Hookform Resolvers)

**UI Components:**
- Radix UI primitives for accessibility
- Lucide React for consistent iconography
- Date-fns for date manipulation
- Class Variance Authority for component variants

**Development Tools:**
- TypeScript for type safety
- Vite for fast development and building
- PostCSS with Tailwind and Autoprefixer

### Backend Dependencies

**Server Framework:**
- Express.js with TypeScript support
- Database connectivity (Drizzle ORM, Neon serverless)
- Session management (connect-pg-simple)

**Development Tools:**
- tsx for TypeScript execution
- esbuild for fast builds
- Development error handling and logging

## Deployment Strategy

### Build Process

**Frontend Build:**
- Vite builds optimized production bundle
- Assets are output to `dist/public` directory
- Static file serving from Express in production

**Backend Build:**
- esbuild bundles server code with external dependencies
- ESM output format for modern Node.js
- Environment-specific configurations

### Environment Configuration

**Development:**
- Hot module replacement via Vite dev server
- In-memory storage for rapid iteration
- Development error overlays and debugging tools

**Production:**
- Static file serving from Express
- PostgreSQL database via environment variables
- Optimized builds with tree shaking

### Database Management

**Schema Management:**
- Drizzle migrations in `./migrations` directory
- Schema definitions in `./shared/schema.ts`
- Push-based deployments with `drizzle-kit push`

**Environment Variables:**
- `DATABASE_URL` for PostgreSQL connection
- `NODE_ENV` for environment detection
- Development vs production configurations