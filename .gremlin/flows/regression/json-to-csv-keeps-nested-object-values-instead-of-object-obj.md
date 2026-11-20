---
title: JSON to CSV keeps nested object values instead of [object Object]
type: regression
platforms:
  - web
start: /json-to-csv
source: breaker
status: active
tags:
  - json-to-csv
  - input-abuse
attack: input.nested-structure
bug: BUG-001
fail_first: RUN-20261120-165257-fd08e6
created: 2026-11-20T11:22:57.963Z
---

1. Open the JSON to CSV page
2. Click into 'Your raw JSON'
3. Paste: [{"name":"Alice","email":"alice@example.test","address":{"city":"Paris"}}]

## Expect

- The 'CSV version of your JSON' output contains Alice and alice@example.test
- The CSV output contains the word Paris
- The CSV output does not contain the text [object Object]

## Notes

Breaker's suspicion: src/tools/json-to-csv/json-to-csv.service.ts serializeValue() calls String(value) on every cell. Nested objects never get JSON.stringify or flattening, so any nested field comes out as the literal '[object Object]' and the data is lost without any warning.
