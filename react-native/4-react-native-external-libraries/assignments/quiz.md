# Quiz: React Native External Libraries

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

Try each question closed-book first. Click **Show hint** if you get stuck — hints point you at the relevant lesson section and how to think about the question, without naming the answer.

## Questions

1. What does the Expo SDK provide access to?

- [ ] Only third-party REST APIs
- [ ] The device's system functionalities (contacts, camera, gyroscope, GPS, etc.) via packages
- [ ] A built-in SQL database
- [ ] Pre-made UI themes only

<details>
<summary>Show hint</summary>

- **Where:** [React Native External Libraries](../1-rn-external-libraries.md) — "Expo SDK".
- **Think:** The lesson lists several examples (contacts, camera, gyroscope, GPS) — what category do these all belong to?

</details>

2. Which command is used to install an Expo SDK package (as opposed to a generic npm package)?

- [ ] `npm install <package>`
- [ ] `npx expo install <package>`
- [ ] `yarn global add <package>`
- [ ] `expo create <package>`

<details>
<summary>Show hint</summary>

- **Where:** [React Native External Libraries](../1-rn-external-libraries.md) — "Expo SDK".
- **Think:** The lesson gives this command explicitly, and again later for `expo-camera` specifically.

</details>

3. According to the lesson, what may some Expo SDK packages require beyond just installation?

- [ ] Nothing further — installation is always sufficient
- [ ] Additional configuration and permissions in `app.json`
- [ ] A separate Expo account for each package
- [ ] Rewriting the app in TypeScript

<details>
<summary>Show hint</summary>

- **Where:** [React Native External Libraries](../1-rn-external-libraries.md) — "Expo SDK", last sentence.
- **Think:** The lesson names a specific config file — and the camera example later shows exactly what goes in it.

</details>

4. What does the `CameraView` component from `expo-camera` allow you to do, besides previewing the camera?

- [ ] Only display a static placeholder image
- [ ] Take photos, record videos, and detect barcodes in the preview
- [ ] Send emails
- [ ] Edit photos with filters

<details>
<summary>Show hint</summary>

- **Where:** [React Native External Libraries](../1-rn-external-libraries.md) — "Sample SDK - Phone Camera", first two paragraphs.
- **Think:** The lesson lists three capabilities of `CameraView` — one of them is the focus of this lesson's demo app.

</details>

5. In `app.json`, what is the purpose of the `plugins` array entry for `expo-camera`?

- [ ] To install the package automatically
- [ ] To configure permissions (e.g. camera permission message) needed by the package
- [ ] To set the app's display name
- [ ] To define navigation routes

<details>
<summary>Show hint</summary>

- **Where:** [React Native External Libraries](../1-rn-external-libraries.md) — "Installation", `app.json` snippet.
- **Think:** Look at the key inside the plugin config: `"cameraPermission": "Allow $(PRODUCT_NAME) to access camera."` — what is this string used for when the app launches?

</details>

6. In the sample code, which hook is used to request camera permissions when the component first loads?

- [ ] `useState`
- [ ] `useEffect`
- [ ] `useContext`
- [ ] `useReducer`

<details>
<summary>Show hint</summary>

- **Where:** [React Native External Libraries](../1-rn-external-libraries.md) — sample `App.js`, near the top of the component.
- **Think:** "When the component loads" is the classic use case for one specific hook with an empty dependency array `[]`.

</details>

7. What does `Camera.requestCameraPermissionsAsync()` return, and how is its result used?

- [ ] It returns nothing; permissions are granted automatically
- [ ] It returns a `status`, which is checked against `'granted'` to set `hasPermission`
- [ ] It directly opens the camera app
- [ ] It returns the scanned barcode data

<details>
<summary>Show hint</summary>

- **Where:** [React Native External Libraries](../1-rn-external-libraries.md) — sample `App.js`, `useEffect` block.
- **Think:** Look at the destructuring `const { status } = await Camera.requestCameraPermissionsAsync();` and the line right after it.

</details>

8. If `hasPermission` is `false`, what does the sample app render?

- [ ] The full camera view anyway
- [ ] A `<Text>` saying "No access to camera"
- [ ] A blank white screen
- [ ] An error that crashes the app

<details>
<summary>Show hint</summary>

- **Where:** [React Native External Libraries](../1-rn-external-libraries.md) — sample `App.js`, the `if (hasPermission === false)` block.
- **Think:** Find the conditional check for `false` specifically (separate from the `null` check) and read what it returns.

</details>

9. What triggers the `handleBarCodeScanned` function in the sample app?

- [ ] A button press only
- [ ] The `onBarcodeScanned` event from `CameraView`, when a barcode is detected in the preview
- [ ] A timer that runs every second
- [ ] Manually typing the barcode value

<details>
<summary>Show hint</summary>

- **Where:** [React Native External Libraries](../1-rn-external-libraries.md) — sample `App.js`, `<CameraView ... onBarcodeScanned={...} />` and the explanatory paragraph below the code.
- **Think:** The lesson explicitly says this handler "handles the barcode scanning based on the event ___".

</details>

10. After a barcode is scanned (`scanned` becomes `true`), what does the app show, and what happens if the user presses it?

- [ ] Nothing changes; the camera keeps scanning continuously
- [ ] A "Tap to Scan Again" button appears; pressing it sets `scanned` back to `false`
- [ ] The app closes
- [ ] A new screen opens via React Navigation

<details>
<summary>Show hint</summary>

- **Where:** [React Native External Libraries](../1-rn-external-libraries.md) — sample `App.js`, the line `{scanned && <Button .../>}`.
- **Think:** Look at the `onPress` handler on that `Button` — what does it set `scanned` to, and why would that re-enable `onBarcodeScanned` (since the prop was `scanned ? undefined : handleBarCodeScanned`)?

</details>
