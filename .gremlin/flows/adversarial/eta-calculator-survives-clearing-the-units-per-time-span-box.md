---
title: ETA calculator survives clearing the units-per-time-span box
type: adversarial
platforms:
  - web
start: /eta-calculator
source: breaker
status: active
tags:
  - eta-calculator
  - input-abuse
attack: input.empty-number-divisor
created: 2026-11-20T11:20:35.456Z
---

1. Open the ETA calculator page
2. Under 'Amount of unit consumed by time span', click the first number box (it shows 3)
3. Select all the text in that box and delete it so the box is empty
4. Click an empty part of the page

## Expect

- The 'Amount of element to consume' field is still visible on the page
- The 'Total duration' card is still visible
- The 'It will end' card is still visible
- No text on the page reads 'Invalid', 'NaN' or 'Infinity'

## Notes

Breaker's suspicion: src/tools/eta-calculator/eta-calculator.vue computes durationMs = unitCount / (unitPerTimeSpan / timeSpanMs). Clearing an n-input-number sets it to null, so this becomes x / 0 = Infinity. Then addMilliseconds(startedAt, Infinity) gives an Invalid Date, and date-fns formatRelative throws RangeError('Invalid time value') inside the render. Vue replaces the failed component with an empty comment node, so the whole tool disappears and doesn't come back.
