# Solution: React Native App

## What a complete solution looks like

A full solution to this exercise should include:

1. **Two Expo SDK libraries** — e.g. `expo-camera` for barcode scanning and `expo-location` for GPS
2. **React Navigation** — tab-based or drawer-based navigation switching between the two library screens
3. **Permission handling** — requesting and checking device permissions before accessing hardware

## Example project structure

```
App.js                  ← NavigationContainer + Tab/Drawer navigator
screens/
  CameraScreen.js       ← expo-camera with barcode scanning
  LocationScreen.js     ← expo-location showing current coordinates
```

## Example `App.js`

```jsx
import * as React from "react";
import { NavigationContainer } from "@react-navigation/native";
import { createBottomTabNavigator } from "@react-navigation/bottom-tabs";
import CameraScreen from "./screens/CameraScreen";
import LocationScreen from "./screens/LocationScreen";

const Tab = createBottomTabNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Tab.Navigator>
        <Tab.Screen name="Camera" component={CameraScreen} />
        <Tab.Screen name="Location" component={LocationScreen} />
      </Tab.Navigator>
    </NavigationContainer>
  );
}
```

## Example `screens/CameraScreen.js`

```jsx
import { useState, useEffect } from "react";
import { Text, View, Button, StyleSheet } from "react-native";
import { CameraView, Camera } from "expo-camera";

export default function CameraScreen() {
  const [hasPermission, setHasPermission] = useState(null);
  const [scanned, setScanned] = useState(false);
  const [scannedData, setScannedData] = useState(null);

  useEffect(() => {
    const getPermission = async () => {
      const { status } = await Camera.requestCameraPermissionsAsync();
      setHasPermission(status === "granted");
    };
    getPermission();
  }, []);

  const handleBarCodeScanned = ({ type, data }) => {
    setScanned(true);
    setScannedData(data);
  };

  if (hasPermission === null) return <Text>Requesting camera permission...</Text>;
  if (hasPermission === false) return <Text>No access to camera</Text>;

  return (
    <View style={styles.container}>
      <CameraView
        style={styles.camera}
        onBarcodeScanned={scanned ? undefined : handleBarCodeScanned}
      />
      {scanned && (
        <View style={styles.result}>
          <Text>Scanned: {scannedData}</Text>
          <Button title="Tap to Scan Again" onPress={() => setScanned(false)} />
        </View>
      )}
    </View>
  );
}

const styles = StyleSheet.create({
  container: { flex: 1 },
  camera: { flex: 1 },
  result: { padding: 16, alignItems: "center" },
});
```

## Example `screens/LocationScreen.js`

```jsx
import { useState, useEffect } from "react";
import { Text, View, Button, StyleSheet } from "react-native";
import * as Location from "expo-location";

export default function LocationScreen() {
  const [hasPermission, setHasPermission] = useState(null);
  const [location, setLocation] = useState(null);

  useEffect(() => {
    const getPermission = async () => {
      const { status } = await Location.requestForegroundPermissionsAsync();
      setHasPermission(status === "granted");
    };
    getPermission();
  }, []);

  const getLocation = async () => {
    const loc = await Location.getCurrentPositionAsync({});
    setLocation(loc.coords);
  };

  if (hasPermission === null) return <Text>Requesting location permission...</Text>;
  if (hasPermission === false) return <Text>No access to location</Text>;

  return (
    <View style={styles.container}>
      <Button title="Get My Location" onPress={getLocation} />
      {location && (
        <View style={styles.result}>
          <Text>Latitude: {location.latitude}</Text>
          <Text>Longitude: {location.longitude}</Text>
        </View>
      )}
    </View>
  );
}

const styles = StyleSheet.create({
  container: { flex: 1, alignItems: "center", justifyContent: "center" },
  result: { marginTop: 20, alignItems: "center" },
});
```

## Installation commands

```bash
npx create-expo-app --template blank ReactNativeApp
cd ReactNativeApp
npm install @react-navigation/native @react-navigation/bottom-tabs
npm install react-native-screens react-native-safe-area-context
npx expo install expo-camera expo-location
```

## `app.json` permissions

```json
{
  "expo": {
    "plugins": [
      [
        "expo-camera",
        { "cameraPermission": "Allow $(PRODUCT_NAME) to access camera." }
      ],
      [
        "expo-location",
        { "locationWhenInUsePermission": "Allow $(PRODUCT_NAME) to use your location." }
      ]
    ]
  }
}
```

## Checklist before submitting

- [ ] App runs without errors on Expo Go or Android emulator
- [ ] Both Expo libraries are functional (not just installed)
- [ ] Navigation switches between at least 2 screens
- [ ] Permissions are requested and handled gracefully
- [ ] Code is clean with no unused imports