---
mode: testing
url: http://localhost:5199/eta-calculator
max_steps: 40
tags: [eta-calculator, input-abuse]
---

# ETA calculator survives clearing the units-per-time-span box

<!-- compiled by gremlin from .gremlin/flows/adversarial/eta-calculator-survives-clearing-the-units-per-time-span-box.md (48262a4868a40e7d). Edit the flow, not this file. -->

## Step 1: Open the ETA calculator page
Open the ETA calculator page.

## Step 2: Under 'Amount of unit consumed by time span', click the first n…
Under 'Amount of unit consumed by time span', click the first number box (it shows 3).

## Step 3: Select all the text in that box and delete it so the box is emp…
Select all the text in that box and delete it so the box is empty.

## Step 4: Click an empty part of the page
Click an empty part of the page.

## Check the expected outcome
Verify that the 'Amount of element to consume' field is still visible on the page.
Verify that the 'Total duration' card is still visible.
Verify that the 'It will end' card is still visible.
Verify that no text on the page reads 'Invalid', 'NaN' or 'Infinity'.
