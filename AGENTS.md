# AGENTS.md

This repository is a curated list of wearable app testing resources, plus practical workflows that help contributors and AI coding agents turn those resources into actionable test plans.

## Purpose

Use this repo to:

- find wearable app testing resources by platform and scenario
- produce platform-specific test plans for apps on Wear OS, watchOS, Garmin, and companion-device workflows
- add well-scoped wearable test cases and review guidance
- improve contributions with clear evaluation criteria instead of only raw links

## Contribution rules

Before contributing a resource, ensure:

- it is relevant to wearable app testing, companion-device testing, or platform-specific validation
- the link is live and authoritative, or clearly described as community guidance
- the entry includes platform, device or hardware limitations when relevant
- the description explains how the resource helps with real wearable testing
- the contribution does not include private user data, credentials, or confidential app details

## Agent workflow

When an agent is helping with this repo:

1. Prefer evidence-driven entries over broad claims.
2. Separate general mobile advice from watch-specific or phone-to-watch-specific guidance.
3. Include hardware limitations and simulator limitations whenever relevant.
4. Keep additions focused on testing artifacts, scenarios, or review guidance.
5. Use the templates under `templates/` for new test cases and review submissions.

## Useful files

- `README.md` — curated list and repo overview
- `skills/wearable-test-planner.md` — agent skill for turning repo knowledge into a wearable test matrix
- `skills/wearable-connectivity-debugger.md` — scenario-focused guidance for sync, disconnect, and recovery workflows
- `templates/wearable-test-case-template.md` — reusable structure for adding practical wearable scenarios
- `.github/PULL_REQUEST_TEMPLATE.md` — checklist for contributors

## What not to add

Avoid entries that are:

- generic mobile testing resources without watch or companion-device context
- duplicates of existing items without a meaningful distinction
- unmaintained or outdated references with no clear value
- claims of support without documented platform or hardware evidence
