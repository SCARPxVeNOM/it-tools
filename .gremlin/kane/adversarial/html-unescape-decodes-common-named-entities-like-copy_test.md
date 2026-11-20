---
mode: testing
url: http://localhost:5199/html-entities
max_steps: 40
tags: [html-entities, input-abuse]
---

# HTML unescape decodes common named entities like &copy;

<!-- compiled by gremlin from .gremlin/flows/adversarial/html-unescape-decodes-common-named-entities-like-copy.md (ce07fcb4977199c8). Edit the flow, not this file. -->

## Step 1: Open the Escape / Unescape HTML entities page
Open the Escape / Unescape HTML entities page.

## Step 2: In the 'Unescape html entities' card, clear the 'Your escaped s…
In the 'Unescape html entities' card, clear the 'Your escaped string' box.

## Step 3: Type: &copy; 2024 Caf&eacute; &euro;5
Type: &copy; 2024 Caf&eacute; &euro;5.

## Check the expected outcome
Verify that 'Your string unescaped' shows © 2024 Café €5.
Verify that 'Your string unescaped' does not contain &copy;, &eacute; or &euro;.
