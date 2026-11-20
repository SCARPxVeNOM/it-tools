---
test: ../json-to-csv-gives-output-or-an-error-for-a-single-json-objec_test.md
status: failed
started: 2026-11-20T11:29:10.391Z
duration_s: 54
session_id: b5f455ad-348d-4a49-9e7c-68161753286b
---

# JSON to CSV gives output or an error for a single JSON object — Result

## Step 1: Open the JSON to CSV page ✓ passed (1.49s)
md5: ad604386c7015d76d053fb64dc5a5707
Open the JSON to CSV page.

## Step 2: Click into 'Your raw JSON' ✓ passed (2.12s)
md5: de24ae2e77584602b215ad1ca4e6a45c
Click into 'Your raw JSON'.

## Step 3: Paste: {name:Bob,email:bob@example.test} ✓ passed (0.19s)
md5: 29e2289990d569fee0e75cbdbdb1d8d4
Paste: {"name":"Bob","email":"bob@example.test"}.

## Check the expected outcome ✗ failed (45.6s)
md5: 619d1ff7d19f144eea256c6424463712
Reason: Checkpoint assertion failed: "the page does not stay silent: either the CSV output contains Bob and bob@example.test, or a visible message says the input must be an array" — bug verdict: JSON-to-CSV silently ignores non-array input [application_issue/validation_defect, confidence 0.94]
Verify that the page does not stay silent: either the CSV output contains Bob and bob@example.test, or a visible message says the input must be an array.
Verify that the CSV output area is not empty unless an error message is shown next to the input.
