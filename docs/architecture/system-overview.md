# System Overview

## 🎯 Project Vision
Transform the current personal portfolio microsite into a SaaS platform where users can create their own portfolios and we can monetize through subscriptions and premium features.

## 🏗️ High-Level Architecture

### Frontend (Next.js 14)
- **Public Pages**: Landing page, pricing, documentation
- **Authentication**: Login/signup with Supabase Auth
- **Dashboard**: User portfolio management interface
- **Editor**: Drag-and-drop portfolio builder
- **Templates**: Pre-built portfolio designs

### Backend (Next.js API Routes)
- **Authentication API**: User management
- **Portfolio API**: CRUD operations for portfolios
- **Template API**: Template management
- **Payment API**: Stripe integration
- **Analytics API**: Usage tracking

### Database (Supabase PostgreSQL)
- **Users**: Account information and preferences
- **Portfolios**: User-created portfolios and content
- **Templates**: Available portfolio templates
- **Subscriptions**: Payment and billing data
- **Analytics**: Usage and performance metrics

### External Services
- **Supabase**: Database, authentication, file storage
- **Stripe**: Payment processing and subscription management
- **Vercel**: Hosting and deployment
- **Custom Domain Service**: For user custom domains

## 🔄 User Flow
1. User visits landing page
2. Signs up for free account
3. Chooses template or starts from scratch
4. Customizes portfolio using editor
5. Publishes portfolio with subdomain
6. Optionally upgrades for custom domain/premium features

## 🛡️ Security Considerations
- Row Level Security (RLS) in Supabase
- JWT token authentication
- Input validation and sanitization
- Rate limiting on API endpoints
- HTTPS everywhere
