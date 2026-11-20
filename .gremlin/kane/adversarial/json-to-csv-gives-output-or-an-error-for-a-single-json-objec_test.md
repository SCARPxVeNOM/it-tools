---
mode: testing
url: http://localhost:5199/json-to-csv
max_steps: 40
tags: [json-to-csv, input-abuse]
---

# JSON to CSV gives output or an error for a single JSON object

<!-- compiled by gremlin from .gremlin/flows/adversarial/json-to-csv-gives-output-or-an-error-for-a-single-json-objec.md (b3255dd274e648fe). Edit the flow, not this file. -->

## Step 1: Open the JSON to CSV page
Open the JSON to CSV page.

## Step 2: Click into 'Your raw JSON'
Click into 'Your raw JSON'.

## Step 3: Paste: {name:Bob,email:bob@example.test}
Paste: {"name":"Bob","email":"bob@example.test"}.

## Check the expected outcome
Verify that the page does not stay silent: either the CSV output contains Bob and bob@example.test, or a visible message says the input must be an array.
Verify that the CSV output area is not empty unless an error message is shown next to the input.
