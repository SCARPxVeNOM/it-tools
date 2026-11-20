---
test: ../json-to-csv-keeps-nested-object-values-instead-of-object-obj_test.md
status: passed
started: 2026-11-20T11:34:33.252Z
duration_s: 32
session_id: e3caf3e0-51d7-4674-9e68-a9304282b9e6
---

# JSON to CSV keeps nested object values instead of [object Object] — Result

## Step 1: Open the JSON to CSV page ✓ passed (2.1s)
md5: ad604386c7015d76d053fb64dc5a5707
Open the JSON to CSV page.

## Step 2: Click into 'Your raw JSON' ✓ passed (1.76s)
md5: de24ae2e77584602b215ad1ca4e6a45c
Click into 'Your raw JSON'.

## Step 3: Paste: [{name:Alice,email:alice@example.test,address:{city:Pari… ✓ passed (0.2s)
md5: 0bd06527918f876dbecd5ecafb725f32
Paste: [{"name":"Alice","email":"alice@example.test","address":{"city":"Paris"}}].

## Check the expected outcome ✓ passed (22.5s)
md5: 024c8dac17b78851ad05dab1871572ad
Verify that the 'CSV version of your JSON' output contains Alice and alice@example.test.
Verify that the CSV output contains the word Paris.
Verify that the CSV output does not contain the text [object Object].
