# INVUI Quick Start Guide

## Installation & Setup

### Prerequisites
- Node.js (v18 or higher)
- npm or yarn
- Expo Go app (for testing on mobile)

### Installation
```bash
# Navigate to project directory
cd c:\Users\amulya\Desktop\personal\Project\invui_app

# Install dependencies (if not already installed)
npm install

# Start development server
npm start
```

## Testing the App

### Login
1. Launch the app
2. Enter credentials:
   - **Username**: `Admin`
   - **Password**: `Admin`
3. Tap "Login"

### Production Entry Workflow

1. **Select Product**
   - Choose from: Spindle75, Spindle120, or Spindle200
   - Tap on any product to continue

2. **Select Process**
   - View all processes for selected product
   - Example processes: Cutting, Drilling, Polishing
   - Tap on any process to continue

3. **Select Machine**
   - View all machines for selected process
   - Example machines: Machine 1, Machine 2, Machine 3
   - Tap on any machine to continue

4. **Enter Production Details**
   - **Worker Name**: Enter the worker's name (e.g., "John Doe")
   - **Start Time**: Tap to open time picker, select hours and minutes
   - **End Time**: Tap to open time picker, select hours and minutes
   - **Units Produced**: Enter number of units (e.g., "150")

5. **Submit or Cancel**
   - **Submit**: Saves the production entry and returns to machine list
   - **Cancel**: Discards entry and returns to machine list

6. **Repeat**
   - You'll be back at the Machine Selection screen
   - Can select another machine or tap Back to go to Process Selection
   - Can repeat the workflow multiple times

### Logout
- From the Product Selection screen, tap the red "Logout" button in the top-right
- Confirm logout to return to login screen

## File Structure for Development

### Adding a New Screen
1. Create a new `.tsx` file in `app/(main)/`
2. Add the screen to `app/(main)/_layout.tsx`
3. Update navigation in relevant components

### Adding a New Component
1. Create a new `.tsx` file in `components/`
2. Export the component as default or named export
3. Import and use in your screens

### Modifying Mock Data
Edit `utils/mockData.ts`:
- `mockProducts`: Array of available products
- `mockProcesses`: Object mapping product IDs to processes
- `mockMachines`: Object mapping process IDs to machines

### Updating App Context
If you need to track additional state:
1. Edit `context/AppContext.tsx`
2. Add new state to the `AppState` interface in `types/index.ts`
3. Add new setter functions in the context

## Common Tasks

### Change Default Login Credentials
Edit `context/AuthContext.tsx`:
```typescript
if (username === 'YOUR_USERNAME' && password === 'YOUR_PASSWORD') {
  // Login successful
}
```

### Add New Product
Edit `utils/mockData.ts`:
```typescript
export const mockProducts: Product[] = [
  // ... existing products
  {
    id: '4',
    name: 'New Product',
    description: 'Description here',
  },
];
```

Then add corresponding processes and machines.

### Customize Colors
Edit the `styles` objects in components or use color values:
- Primary: `#0066CC`
- Secondary: `#E8E8E8`
- Danger: `#FF3B30`

### Add Form Validation
Edit `app/(main)/production.tsx` in the `handleSubmit` function

## Troubleshooting

### App won't start
```bash
# Clear Metro bundler cache
expo start --clear

# Or use npm
npm start -- --clear
```

### Port already in use
```bash
# Use a different port
npm start -- --port 8083
```

### Import errors
```bash
# Reinstall dependencies
rm -rf node_modules
npm install
```

### Type errors
```bash
# Compile TypeScript
npx tsc --noEmit
```

## Environment Variables

Currently, the app doesn't use environment variables. To add them:

1. Create a `.env` file in the project root
2. Use `expo-constants` or similar to access variables
3. Import and use in your code

## Building for Production

### Android APK
```bash
eas build --platform android --local
```

### iOS IPA
```bash
eas build --platform ios --local
```

Note: Requires Expo account and EAS CLI

## Learning Resources

- [Expo Router Documentation](https://docs.expo.dev/router/introduction/)
- [React Native Documentation](https://reactnative.dev/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)

## Support

For issues or questions:
1. Check the console output for error messages
2. Verify mock data structure in `utils/mockData.ts`
3. Check navigation paths in screen files
4. Review type definitions in `types/index.ts`
