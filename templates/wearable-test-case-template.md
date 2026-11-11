# Wearable Test Case Template

Use this template for a reproducible wearable-specific test scenario. Remove fields that do not apply and do not invent expected behavior that the product has not defined.

```markdown
## Scenario

[Short, observable scenario name]

## Platform and scope

- Platform / OS version:
- Phone, wearable, and accessory models (if relevant):
- App version/build:
- Communication path (if relevant):

## Risk addressed

[What wearable-specific failure or user impact does this cover?]

## Preconditions

- Pairing / account state:
- Permissions:
- App lifecycle state:
- Network / Bluetooth / accessory state:
- Test data (synthetic or authorized):

## Steps

1. [Action]
2. [Failure or condition introduced]
3. [Recovery action, if any]

## Expected result

[Observable UI, data, and recovery behavior. Link to a product requirement if one defines it.]

## Validation

- Method: automated / simulator / paired devices / physical hardware
- Hardware required and why:
- Evidence to capture:
- Known limitations:

## Pass criteria

- [ ] ...
```

## Example: sync resumes after temporary disconnection

- **Risk:** A queued workout update is lost or applied twice after a paired device reconnects.
- **Setup:** Use the app's documented phone–watch communication path and synthetic workout data. Record the initial state on both devices.
- **Steps:** Start a sync, interrupt the relevant connection, make one documented local change if supported, restore connectivity, and observe reconciliation.
- **Expected result:** Apply the product's documented conflict and retry policy; verify final state and absence of unintended duplicates. If the policy is unspecified, record that as an open product question rather than treating one behavior as universally correct.
- **Validation:** Use a simulator only for behaviors it supports; verify real pairing and radio-dependent recovery on supported hardware.

## Contribution guidance

Keep repository entries concise and link to this template for detailed scenarios. State whether a scenario is platform-specific, what evidence supports it, and which checks need actual hardware.
