---
test: ../json-to-csv-gives-output-or-an-error-for-a-single-json-objec_test.md
status: passed
started: 2026-11-20T11:50:30.493Z
duration_s: 40
session_id: 676edb6c-a3d0-43cb-a673-cd4d0c06f41e
---

# JSON to CSV gives output or an error for a single JSON object — Result

## Step 1: Open the JSON to CSV page ✓ passed (2.1s)
md5: ad604386c7015d76d053fb64dc5a5707
Open the JSON to CSV page.

## Step 2: Click into 'Your raw JSON' ✓ passed (1.87s)
md5: de24ae2e77584602b215ad1ca4e6a45c
Click into 'Your raw JSON'.

## Step 3: Paste: {name:Bob,email:bob@example.test} ✓ passed (0.2s)
md5: 29e2289990d569fee0e75cbdbdb1d8d4
Paste: {"name":"Bob","email":"bob@example.test"}.

## Check the expected outcome ✓ passed (29.7s)
md5: 619d1ff7d19f144eea256c6424463712
Verify that the page does not stay silent: either the CSV output contains Bob and bob@example.test, or a visible message says the input must be an array.
Verify that the CSV output area is not empty unless an error message is shown next to the input.
