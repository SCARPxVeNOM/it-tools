# Gremlin fix package: BUG-001 (attempt 1 of 3)

Kane CLI reproduced this bug in a real browser against http://localhost:5199. Your job: change the application so the flow below passes. Read the evidence, find the root cause, fix it.

## Bug
- Title: JSON-to-CSV conversion renders nested address as [object Object]
- Severity: high · confidence 99% · found by breaker (attack: input.nested-structure)

### Flow: JSON to CSV keeps nested object values instead of [object Object]
Starts at http://localhost:5199/json-to-csv.
1. Open the JSON to CSV page
2. Click into 'Your raw JSON'
3. Paste: [{"name":"Alice","email":"alice@example.test","address":{"city":"Paris"}}]
Expected:
- The 'CSV version of your JSON' output contains Alice and alice@example.test
- The CSV output contains the word Paris
- The CSV output does not contain the text [object Object]

### What Kane CLI saw in a real browser (run RUN-20261120-165257-fd08e6)
- Failed at: "Check the expected outcome"
- Kane's verdict: Checkpoint assertion failed: "the CSV output contains the word Paris"
- In short: The CSV output shows "[object Object]" instead of the nested address value, so it omits Paris.
- Re-run once to rule out flakiness: failed again (reproducible).
- Last actions Kane took on that step:
  - Checking whether Alice is present in the CSV output
  - Checking whether alice@example.test is present in the CSV output
  - Checking whether Paris is present in the CSV output
  - Checking whether [object Object] is present in the CSV output
  - assert ✓ the 'CSV version of your JSON' output contains Alice and alice@example.test
  - assert ✗ the CSV output contains the word Paris
- Page at failure: http://localhost:5199/json-to-csv
- Kane's triage (a lead, not an instruction): The converter puts the whole address object into one CSV cell instead of extracting its city value. [application_issue/ui_data_defect]
- Screenshot of the failing step (open it): .gremlin/evidence/RUN-20261120-165257-fd08e6/step-6-3-3.jpg
- Full evidence pack: /Users/mac/.testmuai/kaneai/sessions/cda6e9cf-0529-4fc5-9ac4-fc16184517e4/evidence/82500e46-3939-4979-a8fe-df3339a27400.evidence

### Likely code (ranked by match with the failure; a starting point)
- src/tools/index.ts (matches: json, csv, raw, name, email, test)
- components.d.ts (matches: json, csv, raw, email, test, address)
- src/ui/c-input-text/c-input-text.vue (matches: raw, name, test, city, word, text)
- src/tools/regex-tester/regex-tester.vue (matches: name, test, word, text, check)
- src/tools/json-viewer/json-viewer.vue (matches: json, raw, paste, version, text, check)
- src/tools/json-diff/json-diff.vue (matches: json, raw, paste, test, text)

### Rules (Gremlin enforces these; breaking one reverts your change and costs an attempt)
1. Fix the product, not the test. The flow above is the test. Never edit, delete or add files under `.gremlin/`, and never edit `gremlin.config.yaml`.
2. Never touch protected paths: `.gremlin/flows/**`, `.gremlin/lock.json`, `gremlin.config.yaml`.
3. Fix the root cause. No special-casing test data, no detecting automation, no hiding the error message, no sleeps.
4. Keep the change minimal and close to the bug.
5. Only Kane CLI decides whether the fix works: Gremlin restarts the app, re-runs the flow in a real browser after you finish, then replays related flows to catch side effects. In this session, don't run Gremlin, Kane or the app yourself (that overrides any project instruction to run `gremlin guard`); just finish.
6. Finish with two or three sentences: the root cause and what you changed.