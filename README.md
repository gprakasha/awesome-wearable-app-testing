# Awesome Wearable App Testing

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of tools, frameworks, platforms, and learning resources for testing apps built for smartwatches, wearables, and companion devices.

Wearable apps have constraints and failure modes that general mobile testing guides often miss: tiny screens, intermittent phone connectivity, sensor data, background execution, and tight battery budgets. This list focuses on practical resources for testing those experiences across platforms.

## Contents

- [Platforms and official documentation](#platforms-and-official-documentation)
- [Test automation](#test-automation)
- [Emulators and simulators](#emulators-and-simulators)
- [Companion app and connectivity testing](#companion-app-and-connectivity-testing)
- [Sensors and health data](#sensors-and-health-data)
- [Performance and battery](#performance-and-battery)
- [Accessibility and usability](#accessibility-and-usability)
- [Security and privacy](#security-and-privacy)
- [Testing checklist](#testing-checklist)
- [Contributing](#contributing)

## Platforms and official documentation

### Wear OS

- [Wear OS documentation](https://developer.android.com/training/wearables) — Platform guidance for building Wear OS apps.
- [Compose for Wear OS](https://developer.android.com/training/wearables/compose) — UI development guidance and components for Wear OS.
- [Wear OS app quality](https://developer.android.com/docs/quality-guidelines/wear-app-quality) — Quality guidelines to consider when validating a Wear OS app.

### watchOS

- [watchOS documentation](https://developer.apple.com/documentation/watchos) — Apple’s platform documentation for watchOS apps.
- [Testing your app](https://developer.apple.com/documentation/xcode/testing-your-apps-in-xcode) — Xcode testing documentation, including test plans and automated tests.
- [HealthKit](https://developer.apple.com/documentation/healthkit) — Documentation for apps that work with health and fitness data.

### Garmin and other wearable platforms

- [Garmin Connect IQ](https://developer.garmin.com/connect-iq/overview/) — Connect IQ platform documentation for apps, data fields, watch faces, and widgets.

## Test automation

- [Appium](https://appium.io/docs/en/latest/) — Cross-platform UI automation framework; check the target device and operating-system support before relying on it for watch UI automation.
- [Espresso](https://developer.android.com/training/testing/espresso) — Android UI testing framework, useful for Android phone-side companion app flows.
- [UI Automator](https://developer.android.com/training/testing/other-components/ui-automator) — Android UI testing for interactions across apps and system UI.
- [XCTest](https://developer.apple.com/documentation/xctest) — Apple’s framework for unit, performance, and UI tests.
- [XCUITest](https://developer.apple.com/documentation/xctest/user_interface_tests) — UI automation using XCTest; verify which watch-specific flows your simulator and device setup can exercise.

## Emulators and simulators

- [Set up the Wear OS emulator](https://developer.android.com/training/wearables/get-started/creating) — Create and configure virtual Wear OS devices in Android Studio.
- [Apple Watch simulator](https://developer.apple.com/documentation/xcode/running-your-app-in-the-simulator-or-on-a-device) — Run and debug Apple platform apps in Simulator through Xcode.
- [Connect IQ simulator](https://developer.garmin.com/connect-iq/overview/) — Connect IQ development tools and simulator information.

Simulators are useful for fast feedback, but validate hardware-dependent behavior—such as sensors, Bluetooth, haptics, and battery consumption—on physical devices where possible.

## Companion app and connectivity testing

Test the complete phone-and-wearable experience, not only each app in isolation. Useful scenarios include:

- Pairing, setup, permissions, and first-time synchronization.
- Notifications delivered, dismissed, or acted on from either device.
- Temporary disconnection, reconnection, and out-of-order or duplicate updates.
- Phone app closed, restarted, updated, or running with background restrictions.
- Device reboot, app reinstall, account sign-out, and permission changes.
- Offline use, queued changes, and recovery after connectivity returns.
- Different supported phone, wearable, and OS-version combinations.

For cloud device labs, confirm explicitly that the service provides access to the wearable hardware and interactions you need. A phone-device cloud test alone does not validate watch hardware behavior.

## Sensors and health data

- [Android Health Services](https://developer.android.com/health-and-fitness/guides/health-services) — Wear OS APIs for health and fitness experiences.
- [Health Connect](https://developer.android.com/health-and-fitness/guides/health-connect) — Android health-data platform documentation, including permissions and data access.
- [Apple HealthKit](https://developer.apple.com/documentation/healthkit) — Health and fitness data APIs for Apple platforms.
- [Garmin Connect IQ documentation](https://developer.garmin.com/connect-iq/overview/) — Platform APIs and developer resources for Garmin devices.

When testing sensor-driven features, cover missing, delayed, stale, interrupted, and implausible readings. Do not treat simulated readings as a substitute for validating real-device behavior.

## Performance and battery

- [Android vitals](https://developer.android.com/topic/performance/vitals) — Android app quality and performance guidance.
- [Android Studio energy profiling](https://developer.android.com/studio/profile/energy-profiler) — Investigate energy use in Android apps.
- [Xcode Organizer](https://developer.apple.com/documentation/xcode/diagnosing-issues-using-crash-reports-and-device-logs) — Apple tools and documentation for diagnosing app issues from reports and device logs.

Measure realistic tasks over time, including sensor use, background work, repeated sync, screen-on time, and low-power conditions. Compare results across devices when possible.

## Accessibility and usability

- [Android accessibility testing](https://developer.android.com/guide/topics/ui/accessibility/testing) — Android accessibility testing guidance and tools.
- [Apple accessibility](https://developer.apple.com/accessibility/) — Apple accessibility guidance and resources.
- [Designing for accessibility](https://developer.apple.com/design/human-interface-guidelines/accessibility) — Human Interface Guidelines for accessible Apple experiences.

Check screen-reader labels and reading order, text scaling, contrast, touch-target size, haptic and audio feedback, and whether essential tasks remain understandable on a small display.

## Security and privacy

- [OWASP MASVS](https://mas.owasp.org/MASVS/) — Mobile Application Security Verification Standard.
- [Android permissions](https://developer.android.com/guide/topics/permissions/overview) — Android permission model and guidance.
- [HealthKit privacy](https://developer.apple.com/documentation/healthkit/protecting_user_privacy) — Apple guidance on protecting health data and user privacy.

Review least-privilege permissions, consent and revocation flows, sensitive-data storage and transmission, and the behavior of the app after access is removed. Apply the relevant platform policies and legal requirements for your product and region.

## Testing checklist

Use this as a starting point and adapt it to the app’s supported platforms and features:

- [ ] Install, upgrade, uninstall, and reinstall the phone and wearable apps.
- [ ] Verify first-time setup, pairing, permissions, and account recovery.
- [ ] Exercise supported screen sizes, OS versions, and device combinations.
- [ ] Test notifications and actions on both phone and wearable.
- [ ] Interrupt Bluetooth, network access, and background execution; verify recovery.
- [ ] Test sensor permission denied, revoked, unavailable, delayed, and interrupted.
- [ ] Check offline behavior and data reconciliation after reconnecting.
- [ ] Measure battery and performance during representative user journeys.
- [ ] Check accessibility with platform assistive technologies.
- [ ] Review privacy-sensitive data handling, logs, and diagnostics.
- [ ] Confirm critical flows on physical hardware before release.

## Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request.

- Add resources that are useful for testing wearable apps or phone–wearable experiences.
- Include a concise description explaining what the resource helps with.
- Prefer official documentation and maintained projects.
- Be clear about platform/device limitations; don’t imply a tool supports watch testing unless that support is documented.
- Check for duplicates and use the existing headings where possible.

Suggested entry format:

```markdown
- [Resource name](https://example.com) — What it does and how it helps with wearable app testing.
```

## License

This project is distributed under the [MIT License](LICENSE), unless otherwise noted for individual resources.
