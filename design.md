# Crypto Tracker - Mobile App Design

## Overview
A real-time cryptocurrency tracking application with user authentication, live price updates via CoinGecko API, and detailed price charts. The app follows iOS Human Interface Guidelines with a dark theme optimized for mobile portrait orientation (9:16) and one-handed usage.

## Screen List

1. **Login Screen** - User authentication entry point
2. **Register Screen** - New user account creation
3. **Home Screen** - List of cryptocurrencies with real-time prices
4. **Detail Screen** - Individual cryptocurrency details with 7-day chart
5. **Profile Screen** - User profile and settings (logout)

## Primary Content and Functionality

### 1. Login Screen
- **Layout**: Centered form with email and password fields
- **Content**: 
  - App logo at top
  - Email input field
  - Password input field (masked)
  - "Login" button (primary action)
  - "Don't have an account? Register" link
- **Functionality**: 
  - Email/password validation
  - Error messages for failed login
  - Loading indicator during authentication
  - Navigate to Home on successful login

### 2. Register Screen
- **Layout**: Centered form with stacked input fields
- **Content**:
  - App logo at top
  - Username input field
  - Email input field
  - Password input field (masked)
  - Confirm password input field (masked)
  - "Register" button (primary action)
  - "Already have an account? Login" link
- **Functionality**:
  - Client-side validation (email format, password strength, matching passwords)
  - Error messages for validation failures
  - Loading indicator during registration
  - Navigate to Login on successful registration

### 3. Home Screen
- **Layout**: Top header with title, main content area with scrollable list, bottom tab bar
- **Content**:
  - Header: "Crypto Tracker" title with profile icon
  - Pull-to-refresh indicator
  - List of crypto cards showing:
    - Crypto name and symbol (BTC, ETH, SOL, BNB, USDT, etc.)
    - Current price in USD
    - 24h change percentage (green for positive, red for negative)
    - Small indicator showing data freshness (Live/last updated time)
  - Each card is tappable to navigate to Detail Screen
- **Functionality**:
  - Real-time price updates every 10 seconds via polling/WebSocket
  - Pull-to-refresh to manually update prices
  - Offline caching with AsyncStorage (shows cached prices with timestamp)
  - Loading state on initial load
  - Error handling for API failures

### 4. Detail Screen
- **Layout**: Header with back button, scrollable content area
- **Content**:
  - Header: Crypto name, symbol, and current price
  - 7-day price chart (line graph)
  - Statistics section:
    - High price (24h)
    - Low price (24h)
    - Trading volume (24h)
  - Data source attribution: "Official data: CoinGecko, [timestamp]"
  - Live indicator (green dot + "Live" text if data < 30 seconds old)
- **Functionality**:
  - Fetch detailed market data from CoinGecko
  - Render interactive 7-day price chart
  - Display high/low/volume statistics
  - Show data freshness indicator
  - Offline support with cached chart data

### 5. Profile Screen
- **Layout**: Simple centered content area
- **Content**:
  - User information display
  - "Logout" button (destructive action)
- **Functionality**:
  - Display logged-in username/email
  - Clear auth token and navigate to Login on logout

## Key User Flows

### Flow 1: New User Registration & First Login
1. User launches app → sees Login Screen
2. User taps "Register" link → navigates to Register Screen
3. User fills in username, email, password, confirm password
4. User taps "Register" button → validation runs, account created, navigates to Login Screen
5. User enters email and password → logs in → navigates to Home Screen

### Flow 2: Existing User Login
1. User launches app → sees Login Screen
2. User enters email and password
3. User taps "Login" button → authentication succeeds → navigates to Home Screen

### Flow 3: Browse Crypto Prices
1. User on Home Screen sees list of cryptocurrencies with current prices
2. Prices update automatically every 10 seconds
3. User can pull-to-refresh to manually update
4. User taps on a crypto card → navigates to Detail Screen

### Flow 4: View Crypto Details & Chart
1. User on Detail Screen sees crypto name, current price, and 7-day chart
2. Chart displays price trend over 7 days
3. Statistics show high, low, and volume data
4. Data source and freshness indicator displayed
5. User taps back button → returns to Home Screen

### Flow 5: Logout
1. User taps profile icon on Home Screen → navigates to Profile Screen
2. User taps "Logout" button → token cleared, navigates to Login Screen

## Color Choices

- **Background**: `#0A0A0A` (dark charcoal - main screen background)
- **Surface/Cards**: `#1A1A1A` (slightly lighter for card elevation)
- **Text Primary**: `#FFFFFF` (white for main text)
- **Text Secondary**: `#A0A0A0` (light gray for secondary text)
- **Accent/Primary**: `#00D4FF` (bright cyan - for buttons and highlights)
- **Success**: `#00C853` (green - for positive price changes)
- **Error/Warning**: `#FF3B30` (red - for negative price changes)
- **Border**: `#2A2A2A` (subtle dividers)
- **Live Indicator**: `#00C853` (green dot)

## Design Principles

1. **Dark Theme**: Optimized for low-light environments, reduces eye strain
2. **High Contrast**: Text and interactive elements stand out clearly against backgrounds
3. **One-Handed Usage**: All interactive elements positioned within thumb reach
4. **Real-Time Feedback**: Users see immediate visual feedback for all actions
5. **Clear Data Hierarchy**: Most important information (price, change %) is prominent
6. **Accessibility**: Large tap targets (minimum 44x44 pt), clear visual states
7. **iOS-Native Feel**: Follows Apple HIG with standard navigation patterns, spacing, and typography
