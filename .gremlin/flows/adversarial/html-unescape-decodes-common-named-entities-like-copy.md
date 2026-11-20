---
title: HTML unescape decodes common named entities like &copy;
type: adversarial
platforms:
  - web
start: /html-entities
source: breaker
status: confirmed
tags:
  - html-entities
  - input-abuse
attack: input.named-entities
bug: BUG-002
fail_first: RUN-20261120-165515-d115e7
created: 2026-11-20T11:25:15.370Z
---

1. Open the Escape / Unescape HTML entities page
2. In the 'Unescape html entities' card, clear the 'Your escaped string' box
3. Type: &copy; 2024 Caf&eacute; &euro;5

## Expect

- 'Your string unescaped' shows © 2024 Café €5
- 'Your string unescaped' does not contain &copy;, &eacute; or &euro;

## Notes

Breaker's suspicion: src/tools/html-entities/html-entities.vue uses lodash unescape(). That function only decodes &amp; &lt; &gt; &quot; and &#39;. Every other named or numeric entity (&copy;, &eacute;, &euro;, &nbsp;, &#169;) is passed through unchanged, which a tool called 'HTML entities' should not do.
