# Zenith Client

Zenith is an early Android-facing interface prototype for a Minecraft Bedrock workspace.

## Current state

- Navigation opens the selected panel in place rather than jumping down the page.
- Appearance preferences (light mode, compact layout, reduced motion, higher contrast) are stored locally on the device.
- Local UI profiles can be added and switched. They are **not** authenticated Microsoft/Xbox/Minecraft accounts.
- Library intentionally remains empty until a real, trusted content source is designed.
- The performance panel controls only UI presentation. It does not claim to tune Android or Minecraft performance.
- The Android APK is produced by GitHub Actions.

## Important authentication and launch limitations

A real Minecraft account login is not just a Microsoft sign-in page. Zenith needs a registered application, the correct Android redirect configuration, a secure OAuth authorization-code flow with PKCE, and the Xbox/Minecraft service exchange required for Minecraft identity. Never enter a Microsoft password into a custom Zenith form. The app currently does not complete that flow.

Read Microsoft's official [authorization-code flow documentation](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow) and [redirect URI configuration](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-redirect-uri) before wiring up authentication. Native Android authentication should use a supported authentication library and the app's registered package/signature configuration. No client secret should be embedded in the APK.

Launching Minecraft Bedrock is also not yet implemented. The Android app needs a tested native Android handoff to the installed Bedrock package and clear handling when Minecraft is absent. A successful APK build alone does not prove sign-in or game launch works.

Minecraft Java and Bedrock are separate platforms. This Android project targets Bedrock. Java-only camera APIs and Java mod/injector techniques cannot simply be applied to Bedrock on Android. Zenith should prefer documented, user-controlled modding APIs and supported add-on formats; arbitrary process injection is not part of this project.

## Build

Pushes to `main` that change the web app trigger the **Build Zenith Android APK** GitHub Actions workflow. Download the APK from the workflow's artifact section.
