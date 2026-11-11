# Awesome Wearable App Testing

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of tools, frameworks, platforms, and learning resources for testing apps built for smartwatches, wearables, and companion devices.

Wearable apps have constraints and failure modes that general mobile testing guides often miss: tiny screens, intermittent phone connectivity, sensor data, background execution, and tight battery budgets. This guide helps developers and QA teams find relevant resources and build practical test plans for those experiences.

## Practical outputs

Beyond curated links, this repo now includes practical wearable testing assets that contributors and AI coding agents can use directly.

- [Wearable test planner](skills/wearable-test-planner.md) — turns a product or user journey into a wearable-focused test matrix
- [Wearable connectivity debugger](skills/wearable-connectivity-debugger.md) — guides sync, disconnect, recovery, and companion-device testing
- [Wearable test case template](templates/wearable-test-case-template.md) — reusable format for real-world wearable scenarios
- [AGENTS.md](AGENTS.md) — repo instructions for contributors and agent-driven work
- [.github/PULL_REQUEST_TEMPLATE.md](.github/PULL_REQUEST_TEMPLATE.md) — contributor checklist for new entries and changes

## Start here

- **Testing a Wear OS app?** Start with [Wear OS documentation](https://developer.android.com/training/wearables), [Compose for Wear OS](https://developer.android.com/training/wearables/compose), and the [Wear OS testing checklist](#wear-os-testing).
- **Testing a watchOS app?** Start with [watchOS documentation](https://developer.apple.com/documentation/watchos), [XCTest](https://developer.apple.com/documentation/xctest), and the [watchOS testing checklist](#watchos-testing).
- **Testing a phone–watch experience?** Review [companion and connectivity testing](#companion-app-and-connectivity-testing), including the platform-specific communication APIs and disconnection scenarios.
- **Testing sensors, health data, battery, or accessibility?** Jump to [sensors and health data](#sensors-and-health-data), [performance and battery](#performance-and-battery), or [accessibility and usability](#accessibility-and-usability).

## Contents

- [Practical outputs](#practical-outputs)
- [Platforms and official documentation](#platforms-and-official-documentation)
- [Platform-focused testing](#platform-focused-testing)
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
- [Wear OS Data Layer](https://developer.android.com/training/wearables/data/overview) — APIs for communication and data sync between a Wear OS device and its paired phone.

### watchOS

- [watchOS documentation](https://developer.apple.com/documentation/watchos) — Apple’s platform documentation for watchOS apps.
- [Testing your app](https://developer.apple.com/documentation/xcode/testing-your-apps-in-xcode) — Xcode testing documentation, including test plans and automated tests.
- [WatchConnectivity](https://developer.apple.com/documentation/watchconnectivity) — Framework for communication between an iPhone app and its paired Apple Watch app.
- [HealthKit](https://developer.apple.com/documentation/healthkit) — Documentation for apps that work with health and fitness data.
- [Core Bluetooth](https://developer.apple.com/documentation/corebluetooth) — APIs for Bluetooth Low Energy communication with accessories.

### Garmin and other wearable platforms

- [Garmin Connect IQ](https://developer.garmin.com/connect-iq/overview/) — Connect IQ platform documentation for apps, data fields, watch faces, and widgets.

## Platform-focused testing

These checklists are starting points, not statements that every behavior can be automated or simulated. Confirm capabilities for the target OS, device, and tool versions, and validate hardware-dependent behavior on physical devices.

### Wear OS testing

- Exercise app installation, upgrade, permissions, and supported watch sizes and OS versions.
- Test phone–watch sync through the Data Layer, including unavailable peers, delayed delivery, duplicate updates, and recovery after reconnecting.
- Test direct BLE accessory flows separately when the app communicates with a peripheral.
- Check notifications and actions, background work, app process termination, and low-power conditions.
- For health and sensor features, cover permission denial/revocation, missing or delayed readings, and interrupted sessions.
- Verify interactions and performance on a physical watch; emulator coverage does not replace checks of real sensors, radios, haptics, and battery use.

### watchOS testing

- Exercise installation, upgrades, supported watch/phone combinations, and permission changes.
- Test WatchConnectivity transfers and messages when the counterpart app is inactive, unavailable, or disconnected; verify eventual delivery and state reconciliation as appropriate to the app.
- Check notification presentation and actions, background execution, and behavior after either app is terminated or relaunched.
- Test HealthKit authorization, denied or revoked access, unavailable data, and handling of incomplete or delayed samples.
- Use Simulator and XCTest/XCUITest for supported flows, then verify pairing, connectivity, sensors, haptics, and battery-related behavior on physical Apple Watch hardware.

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
- Phone or watch app closed, restarted, updated, or running with background restrictions.
- Device reboot, app reinstall, account sign-out, and permission changes.
- Offline use, queued changes, and recovery after connectivity returns.
- Different supported phone, wearable, and OS-version combinations.

### Platform communication resources

- [Wear OS Data Layer overview](https://developer.android.com/training/wearables/data/overview) — Phone–Wear OS app communication; test its sync and delivery semantics separately from direct BLE.
- [Android Bluetooth overview](https://developer.android.com/develop/connectivity/bluetooth) — Android Bluetooth APIs and concepts for apps that communicate with Bluetooth devices.
- [Android Bluetooth permissions](https://developer.android.com/develop/connectivity/bluetooth/permissions) — Permission behavior to include in setup, denial, and recovery tests.
- [Apple WatchConnectivity](https://developer.apple.com/documentation/watchconnectivity) — iPhone–Apple Watch app communication.
- [Apple Core Bluetooth](https://developer.apple.com/documentation/corebluetooth) — Apple Bluetooth Low Energy APIs for accessory communication.

### Disconnection and recovery scenarios

Adapt these cases to the app's communication path and define the expected outcome before testing. Record user-visible status, data integrity, recovery behavior, and whether physical hardware is required.

| Scenario | What to verify |
| --- | --- |
| Bluetooth disabled or permission revoked | The app explains the problem, handles unavailable access safely, and resumes only when access is restored. |
| Watch or peripheral moves out of range or powers off | The app detects loss without hanging, preserves valid local state, and reports connection status appropriately. |
| Connection restored after interruption | Reconnection occurs according to the product's policy; queued changes reconcile without loss or unintended duplication. |
| Phone or watch app is terminated and relaunched | The app restores or re-establishes the connection as designed and does not rely on an in-memory-only state. |
| Phone, watch, or peripheral reboots | Pairing and app state recover as expected; stale sessions are handled safely. |
| Sync is delayed, repeated, or received out of order | Updates are deduplicated or reconciled, and the final state is consistent on both sides. |
| Network is unavailable while Bluetooth remains available (or vice versa) | The app distinguishes the failed link and preserves functionality that does not depend on it. |
| App is upgraded or permissions change during use | The app handles changed capabilities and resumes sync without corrupting data. |

For cloud device labs, confirm explicitly that the service provides access to the wearable hardware and interactions you need. A phone-device cloud test alone does not validate watch hardware behavior.

## Sensors and health data

- [Android Health Services](https://developer.android.com/health-and-fitness/guides/health-services) — Wear OS APIs for health and fitness experiences.
- [Health Connect](https://developer.android.com/health-and-fitness/guides/health-connect) — Android health-data platform documentation, including permissions and data access.
- [Apple HealthKit](https://developer.apple.com/documentation/healthkit) — Health and fitness data APIs for Apple platforms.
- [Garmin Connect IQ documentation](https://developer.garmin.com/connect-iq/overview/) — Platform APIs and developer resources for Garmin devices.

When testing sensor-driven features, cover missing, delayed, stale, interrupted, and implausible readings. Test permission denial and revocation, and do not treat simulated readings as a substitute for real-device validation.

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

Review least-privilege permissions, consent and revocation flows, sensitive-data storage and transmission, and the behavior of the app after access is removed. Apply the relevant platform policies and applicable privacy requirements.

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

## License

This project is distributed under the [MIT License](LICENSE), unless otherwise noted for individual resources.
