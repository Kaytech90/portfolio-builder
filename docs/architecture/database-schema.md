# Database Schema

## 📊 Tables Overview

### Users Table
```sql
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) UNIQUE NOT NULL,
  full_name VARCHAR(255),
  avatar_url TEXT,
  subscription_tier VARCHAR(50) DEFAULT 'free',
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

Portfolios Table

CREATE TABLE portfolios (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  title VARCHAR(255) NOT NULL,
  slug VARCHAR(100) UNIQUE NOT NULL,
  template_id UUID REFERENCES templates(id),
  content JSONB NOT NULL,
  is_published BOOLEAN DEFAULT false,
  custom_domain VARCHAR(255),
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

Templates Table

CREATE TABLE templates (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name VARCHAR(255) NOT NULL,
  description TEXT,
  preview_image_url TEXT,
  template_data JSONB NOT NULL,
  is_premium BOOLEAN DEFAULT false,
  created_at TIMESTAMP DEFAULT NOW()
);

Subscriptions Table

CREATE TABLE subscriptions (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  stripe_subscription_id VARCHAR(255) UNIQUE,
  status VARCHAR(50) NOT NULL,
  current_period_start TIMESTAMP,
  current_period_end TIMESTAMP,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

Analytics Table

CREATE TABLE analytics (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  portfolio_id UUID REFERENCES portfolios(id) ON DELETE CASCADE,
  event_type VARCHAR(100) NOT NULL,
  visitor_ip VARCHAR(45),
  user_agent TEXT,
  referrer TEXT,
  created_at TIMESTAMP DEFAULT NOW()
);

## 🔐 Row Level Security (RLS) Policies

### Users can only access their own data

ALTER TABLE portfolios ENABLE ROW LEVEL SECURITY;
CREATE POLICY "Users can only access their own portfolios" ON portfolios
  FOR ALL USING (auth.uid() = user_id);

Public portfolios are viewable by everyone

CREATE POLICY "Published portfolios are publicly viewable" ON portfolios
  FOR SELECT USING (is_published = true);


## ✅ **What to do:**

1. **Click on your `database-schema.md` file** in GitHub
2. **Click the pencil icon** (Edit this file) 
3. **You should see your existing content** (the Users Table part)
4. **Add everything from "### Portfolios Table" onwards** to complete the file
5. **Commit the changes**

**The file should have ALL the tables and security policies in ONE single file.**

**Does this make sense now?** Let me know when you've completed this step!
