# Artisan Network Mobile App

A comprehensive React Native Expo mobile application connecting service providers (artisans) with customers, managed by admins.

## Features

### For Customers
- Browse services by categories
- Location-based service filtering
- Book appointments with providers
- View provider contact information
- Manage bookings
- Light/Dark theme toggle
- Profile customization

### For Providers
- Showcase services with descriptions and pricing
- Manage service listings (create, edit, delete)
- Accept/decline booking requests
- View booking history
- Add contact information
- Profile and settings management
- Category selection for services

### For Admins
- Dashboard with comprehensive statistics
- Manage categories (CRUD operations)
- Oversee all users, services, and bookings
- Dispute resolution system
- Full system oversight

## Tech Stack

- **Frontend**: React Native with Expo
- **Backend**: Supabase (PostgreSQL database)
- **Authentication**: Supabase Auth (email/password)
- **Navigation**: React Navigation (Stack & Bottom Tabs)
- **State Management**: React Context API
- **Styling**: React Native StyleSheet

## Color Theme

- Primary: Navy Blue (#001F3F)
- Secondary: Orange (#FF6B35)
- Clean, modern UI with smooth animations

## Database Structure

### Tables
- **profiles**: User profiles with role-based access (customer/provider/admin)
- **categories**: Service categories
- **services**: Provider services with pricing and descriptions
- **bookings**: Customer booking requests and status
- **disputes**: Customer-provider disputes managed by admins

### Security
- Row Level Security (RLS) enabled on all tables
- Role-based access policies
- Secure authentication flow

## Installation

```bash
# Install dependencies
npm install

# Start the development server
npm start

# Run on Android
npm run android

# Run on iOS
npm run ios

# Run on Web
npm run web
```

## Environment Variables

The app uses Supabase with pre-configured environment variables in `.env`:
- EXPO_PUBLIC_SUPABASE_URL
- EXPO_PUBLIC_SUPABASE_ANON_KEY

## Project Structure

```
├── src/
│   ├── contexts/          # Auth & Theme contexts
│   ├── navigation/        # Navigation setup
│   ├── screens/
│   │   ├── auth/         # Login & Register
│   │   ├── customer/     # Customer screens
│   │   ├── provider/     # Provider screens
│   │   ├── admin/        # Admin screens
│   │   └── shared/       # Shared screens (Settings)
│   ├── constants/        # Theme colors & constants
│   └── lib/              # Supabase client
├── App.tsx               # Main app entry
└── package.json
```

## Key Features Implemented

✅ Multi-role authentication (Customer, Provider, Admin)
✅ Role-based navigation
✅ Service browsing with category filtering
✅ Location-based service discovery
✅ Booking management system
✅ Provider service management
✅ Admin dashboard with statistics
✅ Category management (Admin)
✅ Dispute resolution system
✅ Light/Dark theme support
✅ Profile customization
✅ Secure database with RLS policies

## Testing Accounts

Create test accounts for each role:
- Customer: Select "Customer" during registration
- Provider: Select "Provider" during registration
- Admin: Select "Admin" during registration

## Notes

- The app uses Expo's managed workflow
- All API calls are secured with Supabase RLS
- Images are referenced but upload functionality noted for future implementation
- Location services require device permissions
- Database migrations are already applied to Supabase

## Future Enhancements

- Image upload to Supabase Storage
- Push notifications for bookings
- In-app messaging
- Payment integration
- Rating and review system
- Advanced search and filters
