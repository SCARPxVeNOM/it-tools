---
test: ../json-to-csv-keeps-nested-object-values-instead-of-object-obj_test.md
status: passed
started: 2026-11-20T11:52:56.808Z
duration_s: 71
session_id: ec4a3550-40b0-4296-94ac-aac2f1c1c29a
---

# JSON to CSV keeps nested object values instead of [object Object] — Result

## Step 1: Open the JSON to CSV page ✓ passed (13s)
md5: ad604386c7015d76d053fb64dc5a5707
Open the JSON to CSV page.

## Step 2: Click into 'Your raw JSON' ✓ passed (12.6s)
md5: de24ae2e77584602b215ad1ca4e6a45c
Click into 'Your raw JSON'.

## Step 3: Paste: [{name:Alice,email:alice@example.test,address:{city:Pari… ✓ passed (18.3s)
md5: 0bd06527918f876dbecd5ecafb725f32
Paste: [{"name":"Alice","email":"alice@example.test","address":{"city":"Paris"}}].

## Check the expected outcome ✓ passed (22.5s)
md5: 024c8dac17b78851ad05dab1871572ad
Verify that the 'CSV version of your JSON' output contains Alice and alice@example.test.
Verify that the CSV output contains the word Paris.
Verify that the CSV output does not contain the text [object Object].
