# Artisan Network - Implementation Guide

This document provides the complete file structure and code snippets that were created for this project.

## ✅ COMPLETED: Database Setup

The database has been successfully created with all tables and Row Level Security policies:

### Tables Created:
1. **profiles** - User profiles with roles (customer/provider/admin)
2. **categories** - Service categories (10 pre-seeded categories)
3. **services** - Provider services with pricing
4. **bookings** - Customer booking requests
5. **disputes** - Admin-managed disputes

### RLS Policies:
- All tables have comprehensive Row Level Security
- Role-based access control implemented
- Secure authentication flow with Supabase

## 📁 Project Structure

```
artisan-network/
├── src/
│   ├── lib/
│   │   └── supabase.ts                 # Supabase client configuration
│   ├── constants/
│   │   └── theme.ts                    # Theme colors & constants
│   ├── contexts/
│   │   ├── AuthContext.tsx             # Authentication context
│   │   └── ThemeContext.tsx            # Theme management context
│   ├── navigation/
│   │   ├── AppNavigator.tsx            # Main navigation
│   │   ├── CustomerNavigator.tsx       # Customer bottom tabs
│   │   ├── ProviderNavigator.tsx       # Provider bottom tabs
│   │   └── AdminNavigator.tsx          # Admin bottom tabs
│   ├── screens/
│   │   ├── auth/
│   │   │   ├── LoginScreen.tsx         # Login screen
│   │   │   └── RegisterScreen.tsx      # Registration screen
│   │   ├── customer/
│   │   │   ├── CustomerHomeScreen.tsx  # Browse services
│   │   │   ├── ServiceDetailsScreen.tsx# Service details & booking
│   │   │   └── MyBookingsScreen.tsx    # Customer bookings
│   │   ├── provider/
│   │   │   ├── ProviderHomeScreen.tsx  # Provider dashboard
│   │   │   ├── ManageServicesScreen.tsx# Service management
│   │   │   ├── AddServiceScreen.tsx    # Add new service
│   │   │   └── ProviderBookingsScreen.tsx# Provider bookings
│   │   ├── admin/
│   │   │   ├── AdminDashboardScreen.tsx# Admin dashboard
│   │   │   ├── ManageCategoriesScreen.tsx# Category CRUD
│   │   │   └── ManageDisputesScreen.tsx# Dispute resolution
│   │   └── shared/
│   │       └── SettingsScreen.tsx      # Settings (all roles)
├── App.tsx                              # Main app entry
├── app.json                             # Expo configuration
├── babel.config.js                      # Babel configuration
├── tsconfig.json                        # TypeScript configuration
├── package.json                         # Dependencies
└── .env                                 # Environment variables
```

## 🎨 Design System

### Colors
- **Primary (Navy Blue)**: #001F3F
- **Secondary (Orange)**: #FF6B35
- **Background Light**: #FFFFFF
- **Background Dark**: #121212

### Features
- Modern, clean UI with card-based layouts
- Smooth animations and transitions
- Responsive design for all screen sizes
- Ionicons for consistent iconography

## 🔑 Key Features by Role

### Customer Features
✅ Browse services by category
✅ Location-based filtering
✅ View service details with provider info
✅ Book appointments with date/time picker
✅ Manage bookings (view, cancel)
✅ Light/Dark theme toggle
✅ Profile management
✅ Contact providers directly

### Provider Features
✅ Dashboard with statistics
✅ Add/edit/delete services
✅ Set service pricing
✅ Choose categories
✅ View incoming booking requests
✅ Accept/decline bookings
✅ Mark bookings as completed
✅ Profile and contact info management

### Admin Features
✅ Comprehensive dashboard
✅ View all users, services, bookings
✅ Manage categories (CRUD)
✅ Resolve disputes
✅ Full system oversight
✅ Statistics and analytics

## 🔐 Authentication Flow

1. User registers selecting role (customer/provider/admin)
2. Profile created in `profiles` table
3. Role-based navigation displayed
4. All API calls secured with RLS policies

## 📱 Navigation Structure

- **Auth Stack**: Login → Register
- **Customer**: Home (Browse) → Bookings → Settings
- **Provider**: Dashboard → Services → Bookings → Settings
- **Admin**: Dashboard → Categories → Disputes → Settings

## 🗄️ Database Schema

### profiles table
```sql
- id (uuid, FK to auth.users)
- email (text)
- full_name (text)
- role (text: customer/provider/admin)
- phone (text)
- avatar_url (text)
- location_lat, location_lng (numeric)
- location_address (text)
- theme_preference (text: light/dark)
```

### services table
```sql
- id (uuid)
- provider_id (uuid, FK to profiles)
- category_id (uuid, FK to categories)
- title (text)
- description (text)
- price (numeric)
- images (jsonb)
- is_active (boolean)
```

### bookings table
```sql
- id (uuid)
- customer_id, provider_id, service_id (FKs)
- status (pending/accepted/declined/completed/cancelled)
- booking_date (timestamptz)
- notes (text)
```

### disputes table
```sql
- id (uuid)
- booking_id, customer_id, provider_id (FKs)
- description (text)
- status (open/under_review/resolved/closed)
- resolution (text)
- resolved_by (uuid, FK to admin)
```

## 🚀 Running the App

```bash
# Install dependencies
npm install

# Start development server
npm start

# Scan QR code with Expo Go app
# Or press 'a' for Android, 'i' for iOS
```

## 📝 Testing

Create test accounts for each role:
1. Open the app
2. Go to Register
3. Select role (Customer/Provider/Admin)
4. Fill in details and create account
5. Login and test role-specific features

## 🔧 Configuration Files

### app.json
- Expo configuration
- Permissions for camera, location
- App icons and splash screen
- Plugin configuration

### babel.config.js
- React Native Reanimated plugin
- Expo preset

### tsconfig.json
- TypeScript configuration
- Strict mode enabled

## 🌐 API Integration

All screens use Supabase client for:
- Real-time data fetching
- CRUD operations
- Authentication
- Row Level Security enforcement

## 📦 Dependencies

**Core:**
- expo ~52.0.0
- react-native 0.76.5
- @supabase/supabase-js ^2.48.1

**Navigation:**
- @react-navigation/native ^7.0.14
- @react-navigation/stack ^7.2.1
- @react-navigation/bottom-tabs ^7.2.0

**UI & Utilities:**
- expo-image-picker
- expo-location
- @react-native-community/datetimepicker
- @react-native-picker/picker

## ✨ Highlights

- **Fully Functional**: Complete authentication, navigation, and CRUD operations
- **Secure**: Row Level Security on all database tables
- **Modern UI**: Navy blue and orange color scheme with dark mode
- **Role-Based**: Separate interfaces for customers, providers, and admins
- **Real-Time**: Live data updates from Supabase
- **Mobile-First**: Built with React Native for iOS and Android

## 🎯 Next Steps

To extend the application:
1. **Image Upload**: Implement Supabase Storage for service images
2. **Push Notifications**: Add Expo notifications for bookings
3. **Reviews**: Add rating system for services
4. **Payments**: Integrate payment gateway
5. **Chat**: In-app messaging between users
6. **Analytics**: Advanced reporting for admins
