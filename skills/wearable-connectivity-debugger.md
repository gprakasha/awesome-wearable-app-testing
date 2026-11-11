---
name: wearable-connectivity-debugger
description: Plan evidence-driven investigation and test coverage for phone–wearable synchronization, pairing, disconnection, and recovery. Use when reviewing companion-device communication paths or reproducing sync failures.
---

# Wearable Connectivity Debugger

Structure investigation and test planning for phone–wearable sync and connectivity failures. Do not assume all platforms use the same transport or delivery guarantees.

## Identify the actual communication path

Establish which mechanisms the app actually uses:

- Wear OS Data Layer between a Wear OS app and its paired phone app
- Apple WatchConnectivity between an iPhone app and its paired watch app
- Core Bluetooth / BLE to an accessory
- the app's own network or cloud synchronization
- a combination of these

Do not treat phone–watch APIs and direct BLE accessory connections as interchangeable. Confirm app-specific semantics and consult the relevant platform documentation when needed.

## Investigation workflow

1. Record platform, app versions, device pairing, communication API, and relevant logs.
2. Establish intended behavior for connectivity loss, retry, queueing, conflict resolution, and user feedback. Mark unspecified behavior as an open product decision.
3. Reproduce one failure condition at a time: peer unavailable, Bluetooth disabled, network unavailable, delayed or repeated messages, backgrounding, process termination, permission change, or device restart.
4. Compare state on both devices before failure, during failure, and after recovery. Check data integrity, duplication, ordering, and user-visible status.
5. Test lifecycle and background states relevant to the platform; do not assume the OS will run work at an exact time.
6. Classify checks as automatable, simulator-only, paired-device, or physical-hardware-dependent and record limitations.

## Scenario checklist

- initial pairing and setup failure
- peer unavailable or temporarily out of range
- Bluetooth disabled or access permission unavailable/revoked
- network unavailable while Bluetooth remains available, and vice versa
- delayed, repeated, or out-of-order updates
- either app backgrounded, terminated, relaunched, or upgraded
- phone, watch, or accessory reboot
- offline changes reconciled after reconnection
- stale sessions, conflicting updates, or duplicate submissions
- device-lab coverage that may not include watch hardware or pairing

## Output format

| Condition | Steps / evidence | Expected app-specific behavior | State integrity check | Validation method / limitation |
| --- | --- | --- | --- | --- |

## Example request

"Review this app's phone–watch sync path and propose a reproducible recovery test matrix. Distinguish the wearable platform API from direct BLE, include evidence to capture on both devices, and flag expected retry behavior that the app does not document."

## Safety and privacy

Use synthetic or explicitly authorized test data. Redact identifiers and health information from logs, screenshots, and reports. Test only devices and accounts you are authorized to use.

## Use in an agent project

This file uses the Agent Skills `SKILL.md` frontmatter convention. To use it, place the file in a skill directory supported by your coding agent (for example, `skills/wearable-connectivity-debugger/SKILL.md` within a project, if the agent recognizes that location). Agent discovery paths and installation commands differ; check the chosen agent's current documentation. The repository copy is a source artifact, not an installer or plugin.
