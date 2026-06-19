# Quiz: Introduction to React Native

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

Try each question closed-book first. Click **Show hint** if you get stuck — hints point you at the relevant lesson section and how to think about the question, without naming the answer.

## Questions

1. What is React Native?

- [ ] A styling library for web-only React apps
- [ ] A cross-platform library for building native mobile apps (iOS and Android) using JavaScript and React
- [ ] A database for mobile apps
- [ ] A replacement for Node.js

<details>
<summary>Show hint</summary>

- **Where:** [Introduction to React Native](../1-intro-to-react-native.md) — "What is React Native and Expo?".
- **Think:** The definition mentions three things: the languages/library it's built on, the platforms it targets, and the word "cross-platform" — put those together.

</details>

2. What is the relationship between React Native projects and Expo?

- [ ] Expo is an alternative to React Native — you choose one or the other
- [ ] React Native projects are built on the Expo development framework, which simplifies mobile app development
- [ ] Expo only works for backend development
- [ ] Expo replaces JavaScript with a new language

<details>
<summary>Show hint</summary>

- **Where:** [Introduction to React Native](../1-intro-to-react-native.md) — "What is React Native and Expo?".
- **Think:** The lesson says RN projects are "built **on**" something — that's a foundation relationship, not an either/or choice.

</details>

3. What is Expo Go primarily used for?

- [ ] Writing React Native code in the browser
- [ ] Testing React Native apps on your own mobile device by scanning a QR code
- [ ] Compiling apps for the App Store automatically
- [ ] Managing your npm dependencies

<details>
<summary>Show hint</summary>

- **Where:** [Introduction to React Native](../1-intro-to-react-native.md) — "What is React Native and Expo?".
- **Think:** The lesson calls it "the fastest way to get up and running" for one specific purpose — testing on what kind of device?

</details>

4. What must be installed/available on your computer before you can use Expo?

- [ ] A Node runtime
- [ ] A PostgreSQL database
- [ ] Android Studio (mandatory for everyone)
- [ ] Xcode on Windows

<details>
<summary>Show hint</summary>

- **Where:** [Introduction to React Native](../1-intro-to-react-native.md) — "What is React Native and Expo?".
- **Think:** The lesson tells you to check this with a specific terminal command (`<tool> -v`). What does that command check the version of?

</details>

5. Which command creates a new React Native app using a blank template?

- [ ] `npm init react-native`
- [ ] `npx create-expo-app --template blank ReactNativeDemo`
- [ ] `npx expo start`
- [ ] `node create-app.js`

<details>
<summary>Show hint</summary>

- **Where:** [Introduction to React Native](../1-intro-to-react-native.md) — "Creating a React Native App".
- **Think:** One of these commands *creates* a project, and another *runs* an existing one. Which is which?

</details>

6. After running `npx expo start`, what is generated that lets you open the app on your phone via Expo Go?

- [ ] An `.apk` file
- [ ] A QR code
- [ ] A password
- [ ] An email invitation

<details>
<summary>Show hint</summary>

- **Where:** [Introduction to React Native](../1-intro-to-react-native.md) — "Running the app".
- **Think:** The lesson describes scanning something with Expo Go's scanner.

</details>

7. If you see a "Network Response Timed Out" error while running `npx expo start`, what option does the lesson suggest adding?

- [ ] `--force`
- [ ] `--tunnel`
- [ ] `--offline`
- [ ] `--reset-cache`

<details>
<summary>Show hint</summary>

- **Where:** [Introduction to React Native](../1-intro-to-react-native.md) — "Running the app" (note at the bottom).
- **Think:** The fix changes *how the network connection is routed* between your computer and your phone — the flag name describes that kind of routing.

</details>

8. Which of these is **not** listed as a benefit of using an Android emulator over a real device?

- [ ] Testing multiple OS versions
- [ ] Mocking device-specific data such as your current location
- [ ] Taking screenshots and sharing your screen with teammates
- [ ] Making your app run faster in production

<details>
<summary>Show hint</summary>

- **Where:** [Introduction to React Native](../1-intro-to-react-native.md) — "Android Studio" benefits list.
- **Think:** Three of these benefits are listed verbatim in the lesson. The remaining option is about *production performance*, which emulators have nothing to do with.

</details>

9. When setting up a virtual device in Android Studio, which device and OS does the lesson recommend for standardisation?

- [ ] Any device, any OS version
- [ ] Pixel XL, with the latest OS version available
- [ ] iPhone 14, iOS 17
- [ ] Samsung Galaxy, Android 9

<details>
<summary>Show hint</summary>

- **Where:** [Introduction to React Native](../1-intro-to-react-native.md) — "Setting up Android Studio".
- **Think:** The lesson names a specific device model "for standardisation" and says to pick the most recent OS available at the time.

</details>

10. After creating a virtual device and starting `npx expo start`, how do you launch your app inside the Android emulator?

- [ ] Drag the project folder into the emulator window
- [ ] Press the option to "Run on Android Device/Emulator" shown by Expo
- [ ] Manually install Expo Go via a web browser inside the emulator first
- [ ] Restart your computer

<details>
<summary>Show hint</summary>

- **Where:** [Introduction to React Native](../1-intro-to-react-native.md) — "Launching Expo Go in Android Emulator".
- **Think:** Expo's CLI output gives you a choice of where to open the app — one of those choices is the emulator itself.

</details>
