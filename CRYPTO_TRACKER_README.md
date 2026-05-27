# Crypto Tracker - React Native Expo App

A real-time cryptocurrency tracking application built with React Native and Expo. Track Bitcoin, Ethereum, Solana, Binance Coin, and Tether prices with live updates, detailed charts, and user authentication.

## 🎯 Features

### Authentication & User Management
- **User Registration**: Create account with username, email, and password
- **User Login**: Secure login with email and password
- **JWT Mock Authentication**: Token-based authentication with AsyncStorage persistence
- **Protected Routes**: Authenticated users can access the app, unauthenticated users see login screen
- **User Profile**: View user information and logout functionality

### Real-Time Cryptocurrency Tracking
- **Live Price Updates**: Prices update every 10 seconds via polling
- **Multiple Cryptocurrencies**: BTC, ETH, SOL, BNB, USDT
- **24h Price Change**: Display percentage change with color coding (green for positive, red for negative)
- **Data Freshness Indicator**: Shows "Live" indicator if data is less than 30 seconds old
- **Pull-to-Refresh**: Manually refresh prices on the home screen
- **Offline Support**: Cached prices with AsyncStorage for offline viewing

### Detailed Cryptocurrency Information
- **7-Day Price Chart**: Interactive line chart showing price trends
- **Market Statistics**: Display high, low, and volume data for the last 24 hours
- **Market Cap**: Show total market capitalization
- **Data Source Attribution**: Display CoinGecko as data source with timestamp

### Design & UX
- **Dark Theme**: Optimized for low-light environments (#0A0A0A background)
- **Responsive Layout**: Mobile-first design for portrait orientation (9:16)
- **One-Handed Usage**: All interactive elements positioned within thumb reach
- **Smooth Navigation**: Stack and Tab navigation with smooth transitions
- **Loading States**: Activity indicators for all async operations
- **Error Handling**: User-friendly error messages and retry options

## 🛠️ Tech Stack

- **Framework**: React Native with Expo SDK 54
- **Language**: TypeScript
- **State Management**: Zustand
- **Navigation**: React Navigation (Stack + Bottom Tabs)
- **Data Fetching**: Axios
- **Charts**: react-native-chart-kit
- **Storage**: AsyncStorage for local persistence
- **API**: CoinGecko API (free, no API key required)
- **Styling**: NativeWind (Tailwind CSS for React Native)

## 📁 Project Structure

```
crypto-tracker/
├── app/
│   ├── screens/
│   │   ├── LoginScreen.tsx          # Login screen with email/password
│   │   ├── RegisterScreen.tsx       # Registration screen
│   │   ├── HomeScreen.tsx           # Crypto list with real-time prices
│   │   ├── DetailScreen.tsx         # Crypto details with chart
│   │   └── ProfileScreen.tsx        # User profile and logout
│   ├── navigation/
│   │   └── RootNavigator.tsx        # Navigation structure (Auth + App stacks)
│   └── _layout.tsx                  # Root layout with providers
├── store/
│   ├── authStore.ts                 # Zustand auth state management
│   └── cryptoStore.ts               # Zustand crypto data state management
├── services/
│   ├── authService.ts               # Auth validation and utilities
│   └── cryptoAPI.ts                 # CoinGecko API integration
├── components/
│   └── screen-container.tsx         # SafeArea wrapper component
├── assets/
│   └── images/
│       ├── icon.png                 # App icon
│       ├── splash-icon.png          # Splash screen icon
│       └── favicon.png              # Web favicon
├── app.config.ts                    # Expo configuration
├── package.json                     # Dependencies
└── tailwind.config.js               # Tailwind CSS configuration
```

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ and npm/pnpm
- Expo CLI: `npm install -g expo-cli`
- iOS Simulator (Mac) or Android Emulator (Windows/Mac/Linux)
- Or Expo Go app on physical device

### Installation

1. **Navigate to project directory**:
   ```bash
   cd /home/ubuntu/crypto-tracker
   ```

2. **Install dependencies** (already done):
   ```bash
   pnpm install
   ```

3. **Start the development server**:
   ```bash
   pnpm dev
   ```

   This will start both the Metro bundler and the backend server.

### Running on Different Platforms

#### iOS Simulator (macOS only)
```bash
pnpm ios
```

#### Android Emulator
```bash
pnpm android
```

#### Expo Go on Physical Device
1. Install Expo Go app from App Store or Google Play
2. Run: `pnpm dev`
3. Scan the QR code with your phone camera (iOS) or Expo Go app (Android)

#### Web Browser
The app will be available at: `http://localhost:8081`

## 📱 Demo Credentials

For testing the authentication flow:

- **Email**: `user1@example.com`
- **Password**: `password123`

Or create a new account with the Register screen.

## 🔐 Authentication

### How It Works

1. **Registration**: 
   - User provides username, email, password, and confirm password
   - Client-side validation checks email format, password strength, and matching passwords
   - Account is stored in mock database (in production, would be on server)

2. **Login**:
   - User enters email and password
   - Credentials are validated against mock database
   - JWT-like token is generated and stored in AsyncStorage
   - User is redirected to home screen

3. **Token Persistence**:
   - Token is saved to AsyncStorage on login
   - Token is restored on app launch
   - User remains logged in between sessions

4. **Logout**:
   - Token is removed from AsyncStorage
   - User is redirected to login screen

### Validation Rules

- **Email**: Must be valid email format (user@example.com)
- **Username**: At least 3 characters, alphanumeric and underscores only
- **Password**: At least 6 characters, must contain letter and number

## 💹 Cryptocurrency Data

### Data Source
All cryptocurrency data comes from **CoinGecko API** (free, no API key required):
- Price data: `/simple/price` endpoint
- Chart data: `/coins/{id}/market_chart` endpoint
- Market statistics: High, low, volume, market cap

### Supported Cryptocurrencies
- **Bitcoin** (BTC)
- **Ethereum** (ETH)
- **Solana** (SOL)
- **Binance Coin** (BNB)
- **Tether** (USDT)

### Update Frequency
- Prices update every 10 seconds via polling
- Manual refresh available with pull-to-refresh
- 5-minute cache duration for offline support

### Offline Support
- Prices are cached to AsyncStorage with timestamp
- If API fails, cached prices are displayed
- Cache is valid for 5 minutes
- Timestamp shows when data was last updated

## 🎨 Color Scheme

| Element | Color | Hex Code |
|---------|-------|----------|
| Background | Dark Charcoal | #0A0A0A |
| Cards/Surface | Lighter Black | #1A1A1A |
| Primary Text | White | #FFFFFF |
| Secondary Text | Light Gray | #A0A0A0 |
| Accent/Buttons | Bright Cyan | #00D4FF |
| Positive Change | Green | #00C853 |
| Negative Change | Red | #FF3B30 |
| Borders | Subtle Gray | #2A2A2A |

## 📊 Screens Overview

### 1. Login Screen
- Email and password input fields
- Form validation with error messages
- Demo credentials display
- Link to registration screen
- Loading indicator during authentication

### 2. Register Screen
- Username, email, password, and confirm password fields
- Real-time validation feedback
- Password requirements display
- Link to login screen
- Loading indicator during registration

### 3. Home Screen
- List of cryptocurrencies with current prices
- 24-hour price change percentage (color-coded)
- Data freshness indicator (Live/time ago)
- Pull-to-refresh functionality
- Tap to view detailed information
- Real-time updates every 10 seconds

### 4. Detail Screen
- Crypto name, symbol, and current price
- 7-day interactive price chart
- Market statistics (high, low, volume, market cap)
- Data source attribution with timestamp
- Live indicator (green dot if data < 30 seconds old)
- Back button to return to list

### 5. Profile Screen
- Display logged-in user information
- Username and email
- Logout button
- App information section

## 🔄 Navigation Flow

```
Login/Register
    ↓
Home Screen (Tab 1)
    ↓
Detail Screen
    ↓
Back to Home
    ↓
Profile Screen (Tab 2)
    ↓
Logout → Back to Login
```

## 🧪 Testing

### Test Scenarios

1. **Authentication Flow**:
   - Register new account
   - Login with credentials
   - Verify token persistence
   - Logout and verify redirect

2. **Cryptocurrency Data**:
   - Verify prices load on home screen
   - Check real-time updates every 10 seconds
   - Test pull-to-refresh
   - Verify offline caching

3. **Navigation**:
   - Navigate between home and detail screens
   - Switch between tabs
   - Verify back button functionality
   - Test logout from profile

4. **Error Handling**:
   - Disable internet and verify offline cache
   - Test invalid login credentials
   - Test invalid registration data
   - Verify error messages display

## 🐛 Troubleshooting

### App Won't Start
- Clear cache: `rm -rf .expo`
- Reinstall dependencies: `rm -rf node_modules && pnpm install`
- Restart Metro: `pnpm dev`

### Can't Connect to API
- Check internet connection
- Verify CoinGecko API is accessible
- Check if running behind proxy
- Try again - API might be rate-limited

### Login Not Working
- Verify email format is correct
- Check password contains letter and number
- Try demo credentials first
- Clear AsyncStorage: `AsyncStorage.clear()`

### Chart Not Displaying
- Ensure react-native-chart-kit is installed
- Check if chart data is loading (look for loading indicator)
- Verify CoinGecko market_chart endpoint is accessible

### Performance Issues
- Reduce update frequency from 10 seconds if needed
- Limit number of cryptocurrencies displayed
- Use FlatList instead of ScrollView for long lists
- Optimize images and assets

## 📦 Dependencies

Key dependencies used in this project:

- **expo**: React Native framework
- **react-native**: Core React Native library
- **react-navigation**: Navigation library
- **zustand**: State management
- **axios**: HTTP client
- **react-native-chart-kit**: Chart visualization
- **@react-native-async-storage/async-storage**: Local storage
- **nativewind**: Tailwind CSS for React Native
- **react-native-gesture-handler**: Gesture handling

## 🚀 Deployment

### Build for Production

**iOS**:
```bash
eas build --platform ios
```

**Android**:
```bash
eas build --platform android
```

### Publish to App Stores
- Use Expo Application Services (EAS) for building and publishing
- Configure app.json with store details
- Follow Expo documentation for store submission

## 📚 API Documentation

### CoinGecko API Endpoints Used

1. **Get Current Prices**:
   ```
   GET /simple/price?ids=bitcoin,ethereum&vs_currencies=usd&include_24hr_change=true
   ```

2. **Get Market Chart Data**:
   ```
   GET /coins/bitcoin/market_chart?vs_currency=usd&days=7
   ```

3. **Get Detailed Market Data**:
   ```
   GET /simple/price?ids=bitcoin&vs_currencies=usd&include_market_cap=true&include_24hr_vol=true&include_high_low_24h=true
   ```

## 🤝 Contributing

To add new features or improvements:

1. Create a new branch
2. Make changes
3. Test thoroughly
4. Submit pull request

## 📝 License

This project is provided as-is for educational and personal use.

## 🆘 Support

For issues or questions:
1. Check the troubleshooting section
2. Review the code comments
3. Check CoinGecko API documentation
4. Review React Navigation documentation

## 🎓 Learning Resources

- [React Native Documentation](https://reactnative.dev)
- [Expo Documentation](https://docs.expo.dev)
- [React Navigation](https://reactnavigation.org)
- [Zustand Documentation](https://github.com/pmndrs/zustand)
- [CoinGecko API](https://www.coingecko.com/en/api/documentation)
- [NativeWind Documentation](https://www.nativewind.dev)

---

**Created with ❤️ for cryptocurrency enthusiasts**
