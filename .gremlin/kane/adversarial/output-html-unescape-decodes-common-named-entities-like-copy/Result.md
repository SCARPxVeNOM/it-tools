---
test: ../html-unescape-decodes-common-named-entities-like-copy_test.md
status: failed
started: 2026-11-20T11:26:49.190Z
duration_s: 39
session_id: 8eb176d3-6368-4002-9864-83ac0ec9b968
---

# HTML unescape decodes common named entities like &copy; — Result

## Step 1: Open the Escape / Unescape HTML entities page ✓ passed (1.64s)
md5: d6df1a49e2517676dc8e24233ad0c545
Open the Escape / Unescape HTML entities page.

## Step 2: In the 'Unescape html entities' card, clear the 'Your escaped s… ✓ passed (1.63s)
md5: 0a2befa68cc978a482e8d830cdccd8c9
In the 'Unescape html entities' card, clear the 'Your escaped string' box.

## Step 3: Type: &copy; 2024 Caf&eacute; &euro;5 ✓ passed (0.22s)
md5: 121dfa87776d19872fb504bea2293ab3
Type: &copy; 2024 Caf&eacute; &euro;5.

## Check the expected outcome ✗ failed (30.2s)
md5: 66ed4ea7837f0a5d04f892dedc91aaa8
Reason: Checkpoint assertion failed: "'Your string unescaped' shows © 2024 Café €5." — bug verdict: HTML entity unescape output remains encoded [application_issue/functional_defect, confidence 0.98]
Verify that 'Your string unescaped' shows © 2024 Café €5.
Verify that 'Your string unescaped' does not contain &copy;, &eacute; or &euro;.
