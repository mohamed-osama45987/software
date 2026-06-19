# Quiz: React Native Components

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

Try each question closed-book first. Click **Show hint** if you get stuck — hints point you at the relevant lesson section and how to think about the question, without naming the answer.

## Questions

1. Which component is described as "the most fundamental component for building a UI" in React Native?

- [ ] Text
- [ ] View
- [ ] Image
- [ ] ScrollView

<details>
<summary>Show hint</summary>

- **Where:** [React Native Components](../1-rn-components.md) — Introduction and "View and Text Components".
- **Think:** The lesson uses this exact phrase to describe one component — search for "fundamental".

</details>

2. Where must components like `Text` and `View` be imported from before use?

- [ ] `react`
- [ ] `react-native`
- [ ] `expo`
- [ ] `react-dom`

<details>
<summary>Show hint</summary>

- **Where:** [React Native Components](../1-rn-components.md) — "View and Text Components".
- **Think:** Look at the `import { Text, View } from "..."` line in the code sample.

</details>

3. What does the lesson say `View` maps to on the underlying native platform?

- [ ] A web `<div>` only
- [ ] The native view equivalent on whatever platform RN is running on (e.g. `UIView`, `android.view`)
- [ ] A SQL table row
- [ ] Nothing — it's purely virtual and has no native counterpart

<details>
<summary>Show hint</summary>

- **Where:** [React Native Components](../1-rn-components.md) — "View and Text Components".
- **Think:** This is the key idea behind "native" in React *Native* — components correspond to real platform-level UI elements.

</details>

4. If text appears too small on a given screen, what does the lesson suggest as a fix?

- [ ] Reinstall Expo
- [ ] Use an inline style to increase `fontSize` on the `Text` component
- [ ] Switch to the `View` component instead of `Text`
- [ ] Change the phone's system font size

<details>
<summary>Show hint</summary>

- **Where:** [React Native Components](../1-rn-components.md) — "View and Text Components", the note about font size.
- **Think:** The fix is shown directly as a one-line code snippet using `style={{ ... }}`.

</details>

5. When adding a **local** image (from the `assets` folder), how is the image typically referenced in code?

- [ ] As a string file path passed directly to `source="..."`
- [ ] By importing it as a variable (e.g. `import sampleImg from "./assets/sampleImg.png"`) and passing that to `source`
- [ ] By embedding the image as base64 text inside the component
- [ ] Local images cannot be displayed in React Native

<details>
<summary>Show hint</summary>

- **Where:** [React Native Components](../1-rn-components.md) — "Adding local images".
- **Think:** Look at how `sampleImg` is obtained before it's used in `<Image source={sampleImg}>`.

</details>

6. When displaying a **network** image (via a `uri`), what extra step does the lesson say is required compared to local images?

- [ ] None — network images work identically to local images
- [ ] You must manually specify the image's dimensions via a style
- [ ] You must convert the image to a local file first
- [ ] Network images require a different component entirely

<details>
<summary>Show hint</summary>

- **Where:** [React Native Components](../1-rn-components.md) — "Adding images from the web".
- **Think:** The lesson has a "Note" in italics specifically about network/data images — what extra `style` properties does the example add (`height`, `width`)?

</details>

7. Which hook is needed to make the `TextInput` component track and update its value?

- [ ] `useEffect`
- [ ] `useContext`
- [ ] `useState`
- [ ] `useReducer`

<details>
<summary>Show hint</summary>

- **Where:** [React Native Components](../1-rn-components.md) — "TextInput and ScrollView Components".
- **Think:** `TextInput` needs a `value` and an `onChangeText` handler — what's the standard React pattern for storing and updating a piece of UI state?

</details>

8. In the `TextInput` example, what are the `value` and `onChangeText` props set to?

- [ ] `value="text"` and `onChangeText="setText"` (as strings)
- [ ] `value={text}` and `onChangeText={setText}`
- [ ] `value={setText}` and `onChangeText={text}`
- [ ] Neither prop is required

<details>
<summary>Show hint</summary>

- **Where:** [React Native Components](../1-rn-components.md) — "TextInput and ScrollView Components", code sample.
- **Think:** `value` should reflect the *current state value*; `onChangeText` should be the *function* that updates that state. Match each prop to the correct half of `const [text, setText] = useState(null)`.

</details>

9. Why might some components become invisible / "pushed off-screen" as more components are added to a `View`?

- [ ] Because `View` has a fixed maximum height and clips overflow content without scrolling
- [ ] Because `Text` components are limited to 5 per screen
- [ ] Because `Image` components automatically hide other components
- [ ] Because of a bug in Expo that can't be fixed

<details>
<summary>Show hint</summary>

- **Where:** [React Native Components](../1-rn-components.md) — "TextInput and ScrollView Components", paragraph before `ScrollView` is introduced.
- **Think:** The very next sentence introduces the *solution* (`ScrollView`) — what problem does a scrollable container solve that a non-scrollable one doesn't?

</details>

10. What change do you make to fix the issue from the previous question, according to the lesson?

- [ ] Add more `<Text>` components
- [ ] Replace the `View` component (the outer container) with `ScrollView`
- [ ] Remove the `Image` component entirely
- [ ] Decrease the `fontSize` of all text

<details>
<summary>Show hint</summary>

- **Where:** [React Native Components](../1-rn-components.md) — final paragraph.
- **Think:** The lesson's last sentence tells you exactly which component to swap and for what.

</details>
