---
mode: testing
url: http://localhost:5199/json-to-csv
max_steps: 40
tags: [json-to-csv, input-abuse]
---

# JSON to CSV keeps nested object values instead of [object Object]

<!-- compiled by gremlin from .gremlin/flows/adversarial/json-to-csv-keeps-nested-object-values-instead-of-object-obj.md (e8879816cf9b6bff). Edit the flow, not this file. -->

## Step 1: Open the JSON to CSV page
Open the JSON to CSV page.

## Step 2: Click into 'Your raw JSON'
Click into 'Your raw JSON'.

## Step 3: Paste: [{name:Alice,email:alice@example.test,address:{city:Pari…
Paste: [{"name":"Alice","email":"alice@example.test","address":{"city":"Paris"}}].

## Check the expected outcome
Verify that the 'CSV version of your JSON' output contains Alice and alice@example.test.
Verify that the CSV output contains the word Paris.
Verify that the CSV output does not contain the text [object Object].
