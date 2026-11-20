---
title: JSON to CSV gives output or an error for a single JSON object
type: adversarial
platforms:
  - web
start: /json-to-csv
source: breaker
status: confirmed
tags:
  - json-to-csv
  - input-abuse
attack: input.non-array-json
bug: BUG-003
fail_first: RUN-20261120-165733-3950ea
created: 2026-11-20T11:27:33.922Z
---

1. Open the JSON to CSV page
2. Click into 'Your raw JSON'
3. Paste: {"name":"Bob","email":"bob@example.test"}

## Expect

- The page does not stay silent: either the CSV output contains Bob and bob@example.test, or a visible message says the input must be an array
- The CSV output area is not empty unless an error message is shown next to the input

## Notes

Breaker's suspicion: In src/tools/json-to-csv/json-to-csv.vue, the validation rule only checks that JSON5.parse(v) is truthy, so a plain object passes and no error is shown. convertArrayToCsv then calls array.map on that object, which throws. withDefaultOnError catches it and returns '', so the user gets an empty output and no explanation.
