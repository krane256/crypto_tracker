# Crypto Tracker - Project TODO

## Authentication & User Management
- [x] Mock JWT authentication service with token storage
- [x] Login screen with email/password validation
- [x] Register screen with username, email, password, confirm password
- [x] Client-side form validation (email format, password strength)
- [x] AsyncStorage integration for token persistence
- [x] Protected routes - redirect to login if no token
- [x] Profile screen with user info and logout button
- [x] Logout functionality - clear token and navigate to login

## State Management
- [x] Zustand store setup for auth state
- [x] Zustand store setup for crypto data state
- [x] Auth store: login, register, logout, token management
- [x] Crypto store: prices, selected crypto, chart data, loading states
- [x] Persist auth state to AsyncStorage

## Navigation
- [x] React Navigation setup with Stack and Bottom Tabs
- [x] Auth stack (Login, Register screens)
- [x] App stack (Home, Detail, Profile screens)
- [x] Conditional rendering based on auth state
- [x] Tab bar with Home and Profile tabs
- [x] Navigation between screens

## CoinGecko API Integration
- [x] Create cryptoAPI service for fetching price data
- [x] Implement /simple/price endpoint for real-time prices (BTC, ETH, SOL, BNB, USDT)
- [x] Implement /coins/{id}/market_chart endpoint for 7-day chart data
- [x] Polling mechanism - update prices every 10 seconds
- [x] Error handling and retry logic
- [x] Offline caching with AsyncStorage and timestamps
- [x] Data freshness indicator (Live if < 30 seconds old)

## Home Screen
- [x] Display list of cryptocurrencies with prices
- [x] Show 24h price change percentage (green/red colors)
- [x] Pull-to-refresh functionality
- [x] Loading indicator on initial load
- [x] Real-time price updates every 10 seconds
- [x] Tap to navigate to Detail Screen
- [x] Offline support with cached prices
- [x] Last updated timestamp display

## Detail Screen
- [x] Display crypto name, symbol, and current price
- [x] Fetch and render 7-day price chart using react-native-chart-kit
- [x] Display high/low/volume statistics from CoinGecko
- [x] Data source attribution: "Official data: CoinGecko, [timestamp]"
- [x] Live indicator (green dot) if data < 30 seconds old
- [x] Back button navigation
- [x] Offline support with cached chart data

## UI Components
- [x] CryptoCard component for list items (inline in HomeScreen)
- [x] Price chart component with 7-day data
- [x] Loading spinner/indicator
- [x] Error message display
- [x] Input field components (email, password, text)
- [x] Button components (primary, secondary)
- [x] Tab bar with icons

## Styling & Theme
- [x] Dark theme implementation (#0A0A0A background, #1A1A1A cards)
- [x] Color scheme: green for positive, red for negative changes
- [x] Tailwind CSS configuration with custom colors
- [x] Responsive design for mobile portrait (9:16)
- [x] Consistent spacing and typography

## App Configuration
- [x] App icon and splash screen
- [x] App name and branding
- [x] app.config.ts configuration
- [x] Environment variables setup

## Documentation & Delivery
- [x] Comprehensive README with setup instructions
- [x] Demo credentials documentation
- [x] API integration documentation
- [x] Troubleshooting guide
- [x] Project structure documentation
