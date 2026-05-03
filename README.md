# eCop Web Application

A comprehensive Next.js-based web application for managing traffic enforcement, violations, payments, and police operations. Built with TypeScript, MongoDB, and Stripe integration.

## Overview

eCop WebApp is a full-stack web application that provides administrative and operational dashboards for traffic enforcement personnel. It enables management of license holders, violation records, payments, and police officer administration.

## Features

- **Authentication & Authorization**: Next.js Auth with role-based access control
- **User Management**: License holder and police officer profiles
- **Violation Management**: Create, track, and manage traffic violations
- **Payment Processing**: Stripe integration for fine payments
- **Admin Panel**: Manage rules, violations, and approvals
- **Data Persistence**: MongoDB with Mongoose ODM
- **Email Notifications**: Nodemailer integration for alerts
- **SMS Integration**: Twilio for SMS notifications
- **Vonage Integration**: Server SDK for additional communication
- **Type Safety**: Full TypeScript implementation
- **Responsive Design**: Tailwind CSS for modern UI

## Prerequisites

- Node.js (v18+) and npm/yarn
- MongoDB database (local or Atlas)
- Stripe account for payment processing
- Twilio account for SMS (optional)
- Nodemailer email service credentials
- Environment variables configured

## Installation

1. **Clone and install dependencies**:
   ```bash
   cd webapp
   npm install
   ```

2. **Create `.env.local`** with the following variables:
   ```
   # Database
   MONGODB_URI=your_mongodb_connection_string
   
   # Authentication
   NEXTAUTH_SECRET=your_nextauth_secret
   NEXTAUTH_URL=http://localhost:3000
   
   # Stripe
   STRIPE_SECRET_KEY=your_stripe_secret_key
   NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key
   
   # Twilio (optional)
   TWILIO_ACCOUNT_SID=your_account_sid
   TWILIO_AUTH_TOKEN=your_auth_token
   TWILIO_PHONE_NUMBER=your_phone_number
   
   # Email Service
   EMAIL_USER=your_email
   EMAIL_PASSWORD=your_app_password
   ```

## Development

### Start Development Server

```bash
npm run dev
```

The app will be available at `http://localhost:3000`

### Build for Production

```bash
npm run build
```

### Start Production Server

```bash
npm start
```

### Lint Code

```bash
npm run lint
```

## Project Structure

```
app/
├── api/                 # API routes
├── auth/               # Authentication pages
├── admin/              # Admin dashboard pages
├── pendingApproval/    # Approval workflow pages
├── components/         # Reusable React components
├── types/              # TypeScript type definitions
├── globals.css         # Global styles
├── layout.tsx          # Root layout
├── page.tsx            # Home page
└── not-found.tsx       # 404 page

lib/
├── context/            # React context providers
├── email/              # Email service utilities
├── mongo/              # MongoDB utilities
└── utils.ts            # Helper functions

models/
├── licenceHolder.ts    # License holder schema
├── payment.ts          # Payment schema
├── policeOfficer.ts    # Police officer schema
├── rule.ts             # Traffic rule schema
├── users.ts            # User schema
└── ViolationRecord.ts  # Violation record schema

services/
└── apiServices/        # API service clients
```

## Key Dependencies

| Package | Purpose |
|---------|---------|
| `next@15.0.3` | React framework with file-based routing |
| `mongoose@8.8.4` | MongoDB object modeling |
| `next-auth@4.24.10` | Authentication and authorization |
| `stripe@18.2.1` | Payment processing |
| `twilio@5.7.1` | SMS communication |
| `nodemailer@6.10.1` | Email service |
| `tailwindcss@3.4.16` | Utility-first CSS framework |
| `@vonage/server-sdk@3.21.2` | Vonage communication API |
| `lucide-react` | Icon library |
| `notistack@3.0.2` | Notification management |

## API Routes

The application includes RESTful API routes in the `app/api/` directory for:
- User authentication and session management
- License holder operations
- Violation record management
- Payment processing
- Police officer administration
- Rule management

## Database Models

- **User**: Authentication and user management
- **LicenceHolder**: Traffic violators and license information
- **ViolationRecord**: Traffic violations and fines
- **Payment**: Fine payment transactions
- **PoliceOfficer**: Officers and administrator profiles
- **Rule**: Traffic rules and regulations

## Development Guidelines

- Use TypeScript for type safety throughout
- Follow Next.js 15 app router conventions
- Use Tailwind CSS for styling
- Implement API routes in `app/api/` with proper error handling
- Use Mongoose models for database operations
- Implement proper authentication checks with NextAuth
- Handle payments with Stripe SDK
- Log important events and errors

## Available Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server |
| `npm run build` | Build for production |
| `npm start` | Start production server |
| `npm run lint` | Run ESLint |

## Deployment

### Deploy on Vercel

The easiest way to deploy:

1. Push your code to GitHub
2. Connect your repository to [Vercel](https://vercel.com)
3. Set environment variables in Vercel dashboard
4. Vercel will automatically build and deploy on push

### Deploy on Other Platforms

Ensure these environment variables are set:
- `MONGODB_URI`
- `NEXTAUTH_SECRET`
- `STRIPE_SECRET_KEY`
- All other service credentials

## Environment Configuration

Create `.env.local` (development) or set variables in your deployment platform for production. Never commit `.env.local` to version control.

## Security Notes

- Keep `NEXTAUTH_SECRET` secure and unique
- Use environment variables for all sensitive data
- Implement proper CORS policies
- Validate all API inputs
- Use HTTPS in production
- Keep dependencies updated

## Troubleshooting

### MongoDB Connection Issues
- Verify `MONGODB_URI` connection string
- Check MongoDB server is running
- Ensure network access is allowed if using Atlas

### Stripe Errors
- Verify API keys are correct
- Check Stripe account has required products/prices configured
- Review Stripe logs for detailed error information

### Authentication Issues
- Ensure `NEXTAUTH_SECRET` is set
- Check NextAuth callback URLs match deployment domain
- Verify session storage configuration

## Resources

- [Next.js Documentation](https://nextjs.org/docs)
- [MongoDB & Mongoose Guide](https://mongoosejs.com/docs)
- [NextAuth.js Documentation](https://next-auth.js.org)
- [Stripe API Reference](https://stripe.com/docs/api)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
