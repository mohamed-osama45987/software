# Quiz: React Native Navigation

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

Try each question closed-book first. Click **Show hint** if you get stuck — hints point you at the relevant lesson section and how to think about the question, without naming the answer.

## Questions

1. In a web browser, what mechanism lets users navigate back to a previous page?

- [ ] A global history stack maintained by the browser
- [ ] React Navigation's bottom tabs
- [ ] The `<Drawer.Screen>` component
- [ ] The `expo-camera` library

<details>
<summary>Show hint</summary>

- **Where:** [React Native Navigation](../1-rn-navigation.md) — Introduction.
- **Think:** The lesson contrasts how web browsers handle "back" with how React Native does — what does the browser maintain that gets popped on "back"?

</details>

2. According to the lesson, does React Native have a built-in global history stack like a web browser?

- [ ] Yes, identical to the browser's
- [ ] No — React Navigation's stack navigator provides this functionality instead
- [ ] Yes, but only on iOS
- [ ] No, and there is no equivalent at all

<details>
<summary>Show hint</summary>

- **Where:** [React Native Navigation](../1-rn-navigation.md) — Introduction.
- **Think:** The lesson explicitly says RN "doesn't have" the browser's built-in concept, then immediately introduces what fills that gap.

</details>

3. What's a key difference the lesson highlights between web browser navigation and React Navigation's stack navigator?

- [ ] React Navigation requires a server; browsers don't
- [ ] The stack navigator provides gestures and animations typical of Android/iOS navigation
- [ ] Browsers support animations but React Navigation doesn't
- [ ] There is no meaningful difference

<details>
<summary>Show hint</summary>

- **Where:** [React Native Navigation](../1-rn-navigation.md) — Introduction.
- **Think:** This is about *user experience* during a transition between screens — what do mobile OSes typically show when you switch screens that a browser tab-switch doesn't?

</details>

4. Where does tab-based navigation typically place its tabs?

- [ ] In a hidden side drawer
- [ ] On the bottom of the screen, or on top below the header
- [ ] Always in the top-right corner only
- [ ] Tabs are not visual — they're keyboard shortcuts

<details>
<summary>Show hint</summary>

- **Where:** [React Native Navigation](../1-rn-navigation.md) — Introduction.
- **Think:** The lesson distinguishes tab-based from drawer-based by *where on the screen* each appears.

</details>

5. How does drawer-based navigation typically appear to the user?

- [ ] As permanently visible buttons across the top of the screen
- [ ] As a hidden panel on the left or right side that can be pulled out
- [ ] As a popup modal in the center of the screen
- [ ] As a dropdown menu in the status bar

<details>
<summary>Show hint</summary>

- **Where:** [React Native Navigation](../1-rn-navigation.md) — Introduction.
- **Think:** The word "drawer" is a physical metaphor — what do you do to a drawer to access what's inside it?

</details>

6. Which two npm packages are installed for the **tab-based** navigation example?

- [ ] `@react-navigation/native` and `@react-navigation/bottom-tabs`
- [ ] `@react-navigation/native` and `@react-navigation/drawer`
- [ ] `expo-camera` and `react-native-screens`
- [ ] `react-native-gesture-handler` and `react-native-reanimated`

<details>
<summary>Show hint</summary>

- **Where:** [React Native Navigation](../1-rn-navigation.md) — "Tab-based Navigation → Installation".
- **Think:** Look at the first `npm install` command in the tab-based section — two packages are listed.

</details>

7. In the tab-based navigation code, what does `createBottomTabNavigator()` return, and what is it used for?

- [ ] A `Tab` object, used to define `Tab.Navigator` and `Tab.Screen` components
- [ ] A string used as a route name
- [ ] A CSS stylesheet for the tabs
- [ ] A database connection for storing navigation history

<details>
<summary>Show hint</summary>

- **Where:** [React Native Navigation](../1-rn-navigation.md) — "Creation of Bottom Tabs", code sample.
- **Think:** Look at `const Tab = createBottomTabNavigator();` — then see how `Tab` is used two lines later in the JSX.

</details>

8. What is the role of `<NavigationContainer>` in both the tab and drawer examples?

- [ ] It's an optional decorative wrapper with no functional purpose
- [ ] It serves as the wrapper that contains the navigator (Tab or Drawer)
- [ ] It replaces the need for `App.js`
- [ ] It only works with drawer navigation, not tabs

<details>
<summary>Show hint</summary>

- **Where:** [React Native Navigation](../1-rn-navigation.md) — "Creation of Bottom Tabs" and "Creation of Drawer", both explanatory paragraphs after the code.
- **Think:** Both sections describe `NavigationContainer` with the same word — "serves as a ___ for the [Tab/Drawer] navigation".

</details>

9. Which additional package, not needed for tab navigation, is required for drawer navigation specifically to enable swiping?

- [ ] `react-native-gesture-handler`
- [ ] `axios`
- [ ] `expo-camera`
- [ ] `@react-navigation/bottom-tabs`

<details>
<summary>Show hint</summary>

- **Where:** [React Native Navigation](../1-rn-navigation.md) — "Drawer Navigation → Installation".
- **Think:** The lesson explicitly says "We also need to use [this package] to allow us to use swiping" — compare the drawer install command to the tab install command and spot the extra package.

</details>

10. In the drawer navigation example, what is each screen registered as inside `<Drawer.Navigator>`?

- [ ] `<Drawer.Screen name="..." component={...} />`
- [ ] `<Tab.Screen name="..." component={...} />`
- [ ] `<Route path="..." element={...} />`
- [ ] `<Screen.Drawer />`

<details>
<summary>Show hint</summary>

- **Where:** [React Native Navigation](../1-rn-navigation.md) — "Creation of Drawer", code sample.
- **Think:** This mirrors the `Tab.Screen` pattern from the tab example, but with the `Drawer`-prefixed equivalents created by `createDrawerNavigator()`.

</details>
