# Business Website Demo Generator

## Overview

This is a full-stack web application that allows business owners to create an account and receive a staging preview of a modern, AI-enhanced version of their website. The application generates custom demo websites based on user input, using AI to create compelling content and visuals.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React with TypeScript
- **Routing**: Wouter for client-side routing
- **UI Components**: Radix UI with shadcn/ui component library
- **Styling**: Tailwind CSS with custom design tokens
- **State Management**: TanStack Query (React Query) for server state
- **Forms**: React Hook Form with Zod validation
- **Payment Integration**: Stripe with React Stripe.js

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **Build Tool**: Vite for frontend, esbuild for backend
- **Development**: tsx for TypeScript execution

### Data Storage Solutions
- **Database**: PostgreSQL with Drizzle ORM
- **Connection**: Neon Database serverless driver  
- **Schema**: Shared schema definitions between client and server
- **Migrations**: Drizzle Kit for database migrations
- **Storage Implementation**: DatabaseStorage class with full persistence
- **Date**: July 19, 2025 - Migrated from in-memory to persistent database storage

## Key Components

### Authentication System
- **JWT-based Authentication**: Secure token-based authentication with bcrypt password hashing
- **User Registration/Login**: Complete signup and signin flows with form validation
- **Session Management**: Persistent authentication state with localStorage integration
- **Authorization Headers**: Automatic JWT token inclusion in API requests
- **Protected Routes**: Middleware protection for user-specific endpoints

### Core Entities
1. **Users**: Complete user management with secure authentication
   - Username, email, password (bcrypt hashed)
   - JWT token generation for session management
   - User account creation and authentication flows
2. **Demo Submissions**: Business information and generated demo data with user association
   - Business details (name, URL, email, type, theme)
   - AI-generated content (hero image, headline, about section, services)
   - Demo URL, payment status, and save functionality
   - User ownership and saved demo management

### AI Integration
- **OpenAI Integration**: 
  - DALL-E 3 for hero image generation
  - GPT-4 for website content generation (headlines, copy)
- **Content Generation**: Parallel generation of images and text content

### Payment Processing
- **Stripe Integration**: Payment intents for $299 one-time payments
- **Checkout Flow**: Secure payment processing with success handling

### Template System
- **Look & Feel Templates**: Modern, Professional, Fun & Colorful, Creative & Artistic, Vintage & Classic, Luxury Premium
- **Construction-Specific Templates**: Construction Classic, Construction Modern, Construction Industrial
- **Enhanced Features**: Testimonials, portfolio sections, statistics, interactive elements
- **Dynamic Templates**: React components that render based on theme selection with clickable navigation
- **Responsive Design**: Mobile-first approach with sophisticated gradients and subtle design elements

## Data Flow

1. **User Submission**: Business owner fills out demo form with business details
2. **AI Content Generation**: Parallel requests to OpenAI for image and text generation
3. **Demo Creation**: Unique demo URL generated with AI-enhanced content
4. **Preview**: User views their custom demo website with save functionality
5. **Authentication**: Optional user registration/login for demo saving
6. **Demo Management**: Authenticated users can save, view, and manage their demos
7. **Demo Editing**: Full editing capabilities for all demo sections including text, images, and menu items
8. **Dashboard Access**: User dashboard showing all saved demos with management tools
9. **Payment**: Optional checkout flow to make demo live
10. **Database Storage**: All submissions, user data, and saved demos stored persistently

### Demo Editing System
- **Comprehensive Editor**: Modal-based editing interface with tabbed sections
- **Content Editing**: All text content including business name, headlines, about/services sections
- **Image Management**: Hero image URL editing with preview functionality
- **Navigation Editor**: Dynamic menu item management with add/remove capabilities
- **Real-time Updates**: Changes saved to database and immediately reflected in demo
- **User Ownership**: Only demo owners can edit their saved demos
- **API Integration**: PATCH endpoint for secure demo content updates
- **Inline Editing**: Direct click-to-edit functionality on demo sections for seamless editing experience
- **Section Editors**: Individual section components with hover states, tooltips, and immediate save capability
- **Template Integration**: Modern template updated with inline editing for business name, headline, about, and services sections

## External Dependencies

### Required Services
- **OpenAI API**: For content and image generation (DALL-E 3, GPT-4)
- **Stripe**: Payment processing with public/secret key configuration
- **Neon Database**: PostgreSQL hosting with serverless connections

### Development Tools
- **Replit Integration**: Vite plugins for development environment
- **TypeScript**: Strict type checking across the stack
- **Zod**: Runtime type validation and schema definition

## Deployment Strategy

### Production Build
- **Frontend**: Vite build outputting to `dist/public`
- **Backend**: esbuild bundling server code to `dist/index.js`
- **Static Assets**: Served from the built frontend directory

### Environment Configuration
- **Database URL**: PostgreSQL connection string
- **API Keys**: OpenAI and Stripe credentials
- **Development**: Hot reloading with Vite middleware

### Database Management
- **Schema Sync**: `db:push` command for development schema updates
- **Migrations**: Stored in `./migrations` directory
- **Connection Pooling**: Neon serverless handles connection management

### Domain Connection System
- **DNS Automation**: Cloudflare API integration for automatic DNS record creation
- **Provider Support**: 12 popular DNS providers including GoDaddy, Namecheap, Google Domains
- **Manual Fallback**: Instructions provided for non-API providers
- **Real-time Status**: Live monitoring of domain connection status
- **User Interface**: Integrated domain management within saved demo pages

### User Dashboard System
- **Demo Management**: Comprehensive dashboard for viewing and managing all saved demos
- **Navigation Component**: Top navigation with user menu and logout functionality
- **Demo Statistics**: Cards showing total demos, connected domains, and pending domains
- **Demo Cards**: Visual cards displaying business info, themes, domain status, and creation dates
- **Quick Actions**: Direct links to view demos and external demo URLs

The architecture emphasizes rapid development with modern tooling while maintaining production-ready patterns for deployment and scaling.