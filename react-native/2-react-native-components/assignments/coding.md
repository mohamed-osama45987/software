# Assignment: Profile Card App

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

## Setup

```sh
npx create-expo-app --template blank ProfileCardApp
```

Run with `npx expo start` and test using Expo Go (scan the QR code) or an Android emulator.

## Tasks

Build a single-screen app (`App.js`) that displays an editable "profile card":

1. Layout with `View`, `Text`, `Image`

   - Display a profile picture using an **Image from the web** (any image URL of your choice) with explicit `height` and `width` styles.
   - Below it, display a `Text` with a name (start with any placeholder name), styled with a larger `fontSize`.
   - Below that, display a `Text` showing a short bio/tagline.

2. Editable fields with `TextInput` + `useState`

   - Add a `TextInput` for editing the displayed name. As the user types, the `Text` showing the name above should update **live** to match.
   - Add a second `TextInput` for editing the bio, with the same live-update behaviour.

3. Make it scrollable

   - Add enough additional `Text` elements (e.g. a list of 5–6 "fun facts", each its own `Text`) that the content overflows a typical phone screen.
   - Replace the outer `View` with `ScrollView` so all content remains accessible by scrolling.

4. Styling

   - Use `StyleSheet.create` (not only inline styles) for at least: the image, the inputs, and the container.
   - Give the `TextInput`s a visible border so users can tell where to type (the lesson's example `input` style is a good starting point).

## Deliverable

Submit your project folder (excluding `node_modules`) or a GitHub repo link, plus a screenshot or short screen recording showing the live-update behaviour from Task 2.

## Hints

<details>
<summary>Show hints</summary>

## Task 1 — layout
- **Where:** [React Native Components](../1-rn-components.md) — "View and Text Components", "Image Component → Adding images from the web".
- **Think:** Remember the network-image note: you **must** give it explicit `height`/`width` via `style`, unlike local images which can size themselves. Import `Image` alongside `Text` and `View` from `"react-native"`.
- **Starter:**
  ```js
  import { Text, View, Image, StyleSheet } from "react-native";

  export default function App() {
    return (
      <View style={styles.container}>
        <Image
          style={styles.profileImage}
          source={{ uri: "https://placehold.co/200x200" }}
        />
        <Text style={styles.name}>Your Name</Text>
        <Text>A short bio goes here.</Text>
      </View>
    );
  }

  const styles = StyleSheet.create({
    container: { flex: 1, alignItems: "center", paddingTop: 60 },
    profileImage: { height: 150, width: 150, borderRadius: 75 },
    name: { fontSize: 24, marginTop: 12 },
  });
  ```

## Task 2 — live-updating `TextInput`
- **Where:** [React Native Components](../1-rn-components.md) — "TextInput and ScrollView Components".
- **Think:** You need **two** pieces of state: one for the name, one for the bio. The displayed `<Text>{name}</Text>` and the `<TextInput value={name} onChangeText={setName}>` both reference the **same** state variable — that's what makes it "live". Initialise both state variables with a starting value (not `null`), so the `Text` isn't empty before the user types.
- **Starter:**
  ```js
  import { useState } from "react";

  const [name, setName] = useState("Your Name");
  const [bio, setBio] = useState("A short bio goes here.");

  // <Text style={styles.name}>{name}</Text>
  // <TextInput style={styles.input} value={name} onChangeText={setName} />
  ```

## Task 3 — `ScrollView`
- **Where:** [React Native Components](../1-rn-components.md) — final paragraphs ("certain components are no longer visible... we will make the screen scrollable using the `ScrollView` component").
- **Think:** This is a near-literal find-and-replace: swap the outermost `View` (the one with `flex: 1`) for `ScrollView`. Add several `<Text>` elements with enough content (or `marginBottom`) that the page genuinely overflows on a phone-sized screen — otherwise you won't be able to tell if scrolling works.
- **Starter:**
  ```js
  import { ScrollView } from "react-native";

  // <ScrollView style={styles.container}>
  //   ...all your existing content...
  //   <Text>Fun fact 1: ...</Text>
  //   <Text>Fun fact 2: ...</Text>
  //   ... (5-6 total)
  // </ScrollView>
  ```

## Task 4 — styling
- **Where:** [React Native Components](../1-rn-components.md) — `StyleSheet.create` usage in the `Image` and `TextInput` examples.
- **Think:** `StyleSheet.create({...})` is defined **outside** the component function (it's a constant, not recreated on every render). The lesson's `input` style example (`height`, `margin`, `borderWidth`, `padding`) is directly reusable for both your `TextInput`s.

## Common pitfalls
- Forgetting `useState`'s **initial value** for `name`/`bio` — starting from `null` means `<Text>{name}</Text>` renders nothing until the user types.
- Network images with no `style` (no `height`/`width`) — they won't render visibly, or will render at an unexpected size.
- Swapping `View` for `ScrollView` but forgetting that `ScrollView`'s direct child should typically be content, not another `flex: 1` container with a fixed height — this can cause scrolling to not work as expected. If you hit this, try removing `flex: 1` from the `ScrollView`'s style.
- Two separate `TextInput`s both bound to the *same* state variable by mistake — typing in one will also change the other.

</details>
