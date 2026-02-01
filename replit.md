# Unit Converter App

## Overview

A mobile-first unit conversion application designed for Physics and Chemistry students. The app allows users to convert between pressure, volume, and temperature units with a calculator-style interface, camera-based AI problem solving, and conversion history tracking. Built with React frontend and Express backend, using PostgreSQL for data persistence and Replit Auth for user authentication.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter (lightweight alternative to React Router)
- **State Management**: TanStack React Query for server state, React hooks for local state
- **Styling**: Tailwind CSS with shadcn/ui component library (New York style)
- **Animations**: Framer Motion for smooth transitions and micro-interactions
- **Math Processing**: mathjs library for accurate unit conversions on the client side

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Build System**: Vite for frontend, esbuild for server bundling
- **API Design**: RESTful endpoints defined in `shared/routes.ts` with Zod validation
- **Authentication**: Replit Auth (OpenID Connect) with Passport.js
- **Session Management**: PostgreSQL-backed sessions via connect-pg-simple

### Data Storage
- **Database**: PostgreSQL with Drizzle ORM
- **Schema Location**: `shared/schema.ts` (shared between frontend and backend)
- **Key Tables**:
  - `users` - Replit Auth user profiles
  - `sessions` - Session storage for auth
  - `conversions` - User conversion history
  - `conversations` / `messages` - AI chat storage

### Key Design Patterns
- **Monorepo Structure**: Client code in `/client`, server in `/server`, shared types in `/shared`
- **Type Safety**: Zod schemas for API validation, Drizzle for database types
- **Path Aliases**: `@/` for client src, `@shared/` for shared modules

### AI Integration
- OpenAI integration via Replit AI Integrations for:
  - Image-based problem solving (camera feature)
  - Text-to-speech and speech-to-text capabilities
  - Chat-based explanations

## External Dependencies

### Database
- **PostgreSQL**: Primary database (requires DATABASE_URL environment variable)
- **Drizzle ORM**: Database queries and migrations (`drizzle-kit push` for schema sync)

### Authentication
- **Replit Auth**: OAuth/OpenID Connect authentication
- **Required Environment Variables**:
  - `DATABASE_URL` - PostgreSQL connection string
  - `SESSION_SECRET` - Express session secret
  - `ISSUER_URL` - Replit OIDC issuer (defaults to https://replit.com/oidc)
  - `REPL_ID` - Replit environment identifier

### AI Services
- **OpenAI API** (via Replit AI Integrations):
  - `AI_INTEGRATIONS_OPENAI_API_KEY`
  - `AI_INTEGRATIONS_OPENAI_BASE_URL`

### Frontend Libraries
- **shadcn/ui**: Pre-built accessible UI components (Radix UI primitives)
- **react-webcam**: Camera capture for AI scanning feature
- **mathjs**: Scientific unit conversion calculations
- **date-fns**: Date formatting for history display

### Development Tools
- **Vite**: Frontend dev server with HMR
- **tsx**: TypeScript execution for server
- **Replit Vite plugins**: Runtime error overlay, dev banner, cartographer