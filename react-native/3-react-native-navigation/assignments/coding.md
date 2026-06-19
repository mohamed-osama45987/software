# Assignment: Tab Navigation with Passed Data

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

## Setup

```sh
npx create-expo-app --template blank NavDemoApp
cd NavDemoApp
npm install @react-navigation/native @react-navigation/bottom-tabs
npm install react-native-screens react-native-safe-area-context
```

Run with `npx expo start`.

## Tasks

1. Three-tab navigator

   Set up `createBottomTabNavigator` with **three** screens: `Home`, `Favorites`, and `Profile`. Each should render at minimum a `<Text>` with its own name, exactly as in the lesson's `HomeScreen`/`SettingsScreen` example.

2. A list on the `Home` screen

   On `Home`, render a hardcoded array of at least 5 "item" objects, each with `{ id, title, description }`. Render each item's `title` as a `Text` inside a `View`, using `.map()` over the array (don't hand-write 5 separate `<View>`s).

3. Pass data between screens

   When a user taps an item on `Home`, navigate to a new screen `Details` (you'll need to add this as a fourth `Tab.Screen`, or — for extra challenge — nest a stack navigator inside the `Home` tab so `Details` isn't itself a tab. Either approach is acceptable for this assignment). Pass the tapped item's `id` (and/or the whole item) as a route param, and have `Details` display that item's `title` and `description`.

4. `Favorites` screen with shared state

   On `Home`, add a button on each item that adds that item to a "favorites" list. On the `Favorites` tab, display the titles of all favorited items. Since `Home` and `Favorites` are sibling screens (state in one doesn't automatically reach the other), lift the favorites state up to the top-level `App` component and pass it (and a function to update it) down as **props** to both `HomeScreen` and `FavoritesScreen`.

5. `Profile` screen

   On `Profile`, display any static info you like (e.g. your name, a fun fact). No interactivity required here — this screen exists mainly to confirm your three-tab setup works end-to-end.

## Deliverable

Submit your project folder (excluding `node_modules`) or a GitHub repo link, plus a short screen recording demonstrating: switching tabs, tapping an item to see its details, and favoriting an item that then appears on the `Favorites` tab.

## Hints

<details>
<summary>Show hints</summary>

## Task 1 — three tabs
- **Where:** [React Native Navigation](../1-rn-navigation.md) — "Tab-based Navigation", full code sample.
- **Think:** This is the lesson's example with a third `Tab.Screen` added. Define three separate components (`HomeScreen`, `FavoritesScreen`, `ProfileScreen`) above `App`, then register all three under `<Tab.Navigator>`.
- **Starter:**
  ```js
  import * as React from 'react';
  import { Text, View } from 'react-native';
  import { NavigationContainer } from '@react-navigation/native';
  import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';

  const Tab = createBottomTabNavigator();

  export default function App() {
    return (
      <NavigationContainer>
        <Tab.Navigator>
          <Tab.Screen name="Home" component={HomeScreen} />
          <Tab.Screen name="Favorites" component={FavoritesScreen} />
          <Tab.Screen name="Profile" component={ProfileScreen} />
        </Tab.Navigator>
      </NavigationContainer>
    );
  }
  ```

## Task 2 — rendering a list
- **Where:** [React Native Components](../1-rn-components.md) — `View`/`Text` basics (the navigation lesson doesn't cover lists, so combine with what you know from RN Components and React generally).
- **Think:** `.map()` over your array, returning a `<View key={item.id}>` containing a `<Text>{item.title}</Text>` for each. Every mapped element needs a unique `key` prop — `item.id` is perfect for this.
- **Starter:**
  ```js
  const items = [
    { id: 1, title: "Item One", description: "Description for item one." },
    { id: 2, title: "Item Two", description: "Description for item two." },
    // ... at least 5 total
  ];

  function HomeScreen({ navigation }) {
    return (
      <View>
        {items.map((item) => (
          <View key={item.id}>
            <Text>{item.title}</Text>
          </View>
        ))}
      </View>
    );
  }
  ```

## Task 3 — passing data via navigation
- **Where:** [React Native Navigation](../1-rn-navigation.md) — "Creation of Bottom Tabs" (the `Tab.Screen` pattern); for passing params, this extends what the lesson shows.
- **Think:** Every screen component registered via `Tab.Screen` automatically receives a `navigation` prop. Calling `navigation.navigate("Details", { item })` switches to the `Details` tab/screen *and* makes `{ item }` available there via the `route` prop (`route.params.item`). Wrap each list row in a `Pressable` or `TouchableOpacity` (`from "react-native"`) with `onPress={() => navigation.navigate("Details", { item })}`.
- **Starter:**
  ```js
  import { Pressable } from "react-native";

  // inside HomeScreen's .map():
  <Pressable onPress={() => navigation.navigate("Details", { item })}>
    <Text>{item.title}</Text>
  </Pressable>

  // DetailsScreen
  function DetailsScreen({ route }) {
    const { item } = route.params;
    return (
      <View>
        <Text>{item.title}</Text>
        <Text>{item.description}</Text>
      </View>
    );
  }
  ```

## Task 4 — lifting state for `Favorites`
- **Where:** Not directly covered by either lesson — this combines RN Navigation's screen structure with the general React pattern of "lifting state up" (covered in earlier React modules: state that's shared between siblings lives in their closest common parent).
- **Think:** `App` is the common parent of every tab screen. Put `const [favorites, setFavorites] = useState([])` in `App`, then pass `favorites` and a handler like `addFavorite` down as **extra props** on each `Tab.Screen`'s `component` — but `Tab.Screen` doesn't take arbitrary props directly the way a normal component does. Use the `children` render-prop form of `Tab.Screen` instead of `component` to pass custom props through.
- **Starter:**
  ```js
  export default function App() {
    const [favorites, setFavorites] = useState([]);

    const addFavorite = (item) => {
      setFavorites((prev) => [...prev, item]);
    };

    return (
      <NavigationContainer>
        <Tab.Navigator>
          <Tab.Screen name="Home">
            {(props) => <HomeScreen {...props} addFavorite={addFavorite} />}
          </Tab.Screen>
          <Tab.Screen name="Favorites">
            {(props) => <FavoritesScreen {...props} favorites={favorites} />}
          </Tab.Screen>
          <Tab.Screen name="Profile" component={ProfileScreen} />
        </Tab.Navigator>
      </NavigationContainer>
    );
  }
  ```

## Task 5 — `Profile`
- **Where:** [React Native Navigation](../1-rn-navigation.md) — same `Tab.Screen` pattern as `SettingsScreen` in the lesson's original example.
- **Think:** This is intentionally the simplest screen — if it renders correctly, your `Tab.Navigator` setup from Task 1 is solid.

## Common pitfalls
- Missing `key` props when `.map()`-ing the item list — React will warn, and re-renders may behave unexpectedly.
- Trying to pass props directly via `<Tab.Screen component={HomeScreen} favorites={favorites} />` — `component` doesn't forward extra props; use the `children` function form shown above.
- Forgetting `route.params` can be `undefined` if `Details` is reached without navigating from `Home` first (e.g. if it's a tab someone taps directly) — guard with `route.params?.item`.
- Duplicate favorites if `addFavorite` doesn't check whether the item is already in the list.

</details>
