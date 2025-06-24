# API Design

## 🛣️ API Routes Overview

### Authentication Routes
- `POST /api/auth/signup` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout
- `GET /api/auth/user` - Get current user

### Portfolio Routes
- `GET /api/portfolios` - Get user's portfolios
- `POST /api/portfolios` - Create new portfolio
- `GET /api/portfolios/[id]` - Get specific portfolio
- `PUT /api/portfolios/[id]` - Update portfolio
- `DELETE /api/portfolios/[id]` - Delete portfolio
- `POST /api/portfolios/[id]/publish` - Publish portfolio

### Template Routes
- `GET /api/templates` - Get available templates
- `GET /api/templates/[id]` - Get specific template
- `POST /api/templates` - Create template (admin only)

### Payment Routes
- `POST /api/payments/create-checkout` - Create Stripe checkout
- `POST /api/payments/webhook` - Stripe webhook handler
- `GET /api/payments/subscription` - Get user subscription

### Analytics Routes
- `POST /api/analytics/track` - Track portfolio view
- `GET /api/analytics/[portfolio-id]` - Get portfolio analytics

## 📝 API Response Format

### Success Response
```json
{
  "success": true,
  "data": {
    // Response data
  },
  "message": "Operation completed successfully"
}

Error Response

{
  "success": false,
  "error": {
    "code": "ERROR_CODE",
    "message": "Human readable error message"
  }
}

## 🔒 Authentication

- JWT tokens via Supabase Auth
- Protected routes require valid token
- Rate limiting: 100 requests per minute per user


### **Step 3: Commit the file**
1. **Add commit message**: `"Add API design documentation"`
2. **Click "Commit new file"**

**Let me know when you've completed these steps and I'll guide you to the next file!** 🚀
