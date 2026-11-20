# Gremlin fix package: BUG-003 (attempt 1 of 3)

Kane CLI reproduced this bug in a real browser against http://localhost:5199. Your job: change the application so the flow below passes. Read the evidence, find the root cause, fix it.

## Bug
- Title: JSON-to-CSV silently ignores non-array input
- Severity: high · confidence 94% · found by breaker (attack: input.non-array-json)

### Flow: JSON to CSV gives output or an error for a single JSON object
Starts at http://localhost:5199/json-to-csv.
1. Open the JSON to CSV page
2. Click into 'Your raw JSON'
3. Paste: {"name":"Bob","email":"bob@example.test"}
Expected:
- The page does not stay silent: either the CSV output contains Bob and bob@example.test, or a visible message says the input must be an array
- The CSV output area is not empty unless an error message is shown next to the input

### What Kane CLI saw in a real browser (run RUN-20261120-165733-3950ea)
- Failed at: "Check the expected outcome"
- Kane's verdict: Checkpoint assertion failed: "the page does not stay silent: either the CSV output contains Bob and bob@example.test, or a visible message says the input must be an array"
- In short: Entering a JSON object leaves the CSV output empty without telling the user that an array is required.
- Re-run once to rule out flakiness: failed again (reproducible).
- Last actions Kane took on that step:
  - Checking whether the CSV output area is present
  - Checking whether the CSV output contains the requested values
  - Checking whether the array-input message is visible
  - Checking whether an error message is visible next to the input
  - assert ✗ the page does not stay silent: either the CSV output contains Bob and bob@example.test, or a visible message says the input must be an array
- Page at failure: http://localhost:5199/json-to-csv
- Kane's triage (a lead, not an instruction): The converter received a JSON object rather than an array, but it neither produced CSV nor showed the required validation message. [application_issue/validation_defect]
- Screenshot of the failing step (open it): .gremlin/evidence/RUN-20261120-165733-3950ea/step-5-3-2.jpg
- Full evidence pack: /Users/mac/.testmuai/kaneai/sessions/b5f455ad-348d-4a49-9e7c-68161753286b/evidence/6cf7be63-d17e-48b0-a90a-a4b9898ee01f.evidence

### Likely code (ranked by match with the failure; a starting point)
- src/ui/c-input-text/c-input-text.vue (matches: raw, name, test, input, area, next)
- components.d.ts (matches: json, csv, raw, email, test, input)
- auto-imports.d.ts (matches: object, raw, array, area, next, check)
- src/tools/index.ts (matches: json, csv, raw, name, email, test)
- src/tools/json-to-csv/json-to-csv.vue (matches: json, csv, output, raw, paste, input)
- src/tools/json-viewer/json-viewer.vue (matches: json, raw, paste, input, area, check)

### Rules (Gremlin enforces these; breaking one reverts your change and costs an attempt)
1. Fix the product, not the test. The flow above is the test. Never edit, delete or add files under `.gremlin/`, and never edit `gremlin.config.yaml`.
2. Never touch protected paths: `.gremlin/flows/**`, `.gremlin/lock.json`, `gremlin.config.yaml`.
3. Fix the root cause. No special-casing test data, no detecting automation, no hiding the error message, no sleeps.
4. Keep the change minimal and close to the bug.
5. Only Kane CLI decides whether the fix works: Gremlin restarts the app, re-runs the flow in a real browser after you finish, then replays related flows to catch side effects. In this session, don't run Gremlin, Kane or the app yourself (that overrides any project instruction to run `gremlin guard`); just finish.
6. Finish with two or three sentences: the root cause and what you changed.