---
name: wearable-test-planner
description: Create an evidence-aware, wearable-specific test plan for Wear OS, watchOS, Garmin, and companion-device applications. Use when planning QA coverage, reviewing wearable user journeys, or identifying simulator versus physical-device test needs.
---

# Wearable Test Planner

Turn the app's actual features and user journeys into a prioritized test matrix. Do not assume platform behavior or product requirements that are not evidenced by the repository or supplied context.

## Gather context

Inspect the project or ask the user to identify:

- target platform(s) and supported OS/device versions
- device topology: standalone wearable, paired phone and watch, BLE accessory, or cloud-connected device
- key user journeys and data exchanged
- notification, health, sensor, background-work, and accessibility features
- available simulators, paired devices, and physical hardware

Do not infer watch support from generic mobile code. Record unknowns and ask for clarification when they affect test recommendations.

## Plan tests

1. Map critical journeys and data flows from project evidence.
2. Identify relevant wearable failure modes: tiny-screen interaction, pairing, disconnection, delayed or repeated updates, permissions, background execution, stale sensor data, battery, accessibility, and privacy.
3. Tailor scenarios to the app's actual features. Skip irrelevant categories.
4. For every scenario, specify preconditions, steps, observable expected result, and evidence to collect. If product behavior is unspecified, flag an open product decision instead of inventing an assertion.
5. Classify validation as automated/simulator candidate, paired-device test, or physical-hardware validation. Do not promise automation without confirming the test environment and API support.
6. Prioritize a small set of high-risk gaps and state why they matter.

## Output format

```markdown
## Scope and assumptions
- Platforms/devices:
- Features reviewed:
- Unknowns:

## Prioritized test matrix
| Priority | Scenario | Setup and action | Expected result | Validation method | Evidence |
| --- | --- | --- | --- | --- | --- |

## Hardware-dependent checks
- ...

## Open questions
- ...
```

## Example request

"Inspect this Wear OS workout app and its Android companion. Create a test plan for workout recording and sync, including connection loss, delayed or duplicate updates, denied sensor permissions, app process termination, and accessibility. Separate automated candidates from checks that need a paired physical watch."

## Reality and privacy checks

- A simulator does not establish real radio reliability, sensor accuracy, haptic behavior, or battery life.
- Physical-device testing does not automatically cover all device models, OS versions, or network conditions.
- Do not use personal health data in examples; use synthetic or explicitly authorized test data.
- Report only conclusions supported by project evidence or documented platform behavior; label assumptions.

## Use in an agent project

This file uses the Agent Skills `SKILL.md` frontmatter convention. To use it, place the file in a skill directory supported by your coding agent (for example, `skills/wearable-test-planner/SKILL.md` within a project, if the agent recognizes that location). Agent discovery paths and installation commands differ; check the chosen agent's current documentation. The repository copy is a source artifact, not an installer or plugin.
