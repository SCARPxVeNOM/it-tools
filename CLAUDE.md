<!-- gremlin:start -->
## Gremlin: prove it works before you say it's done

This project is guarded by Gremlin. User flows live in `.gremlin/flows/` as plain English, and Kane CLI runs them in a real browser.

- Before you report a task as done, run `gremlin guard` (or the `gremlin_guard` MCP tool). If it fails, read the evidence it prints, fix the application, and run it again.
- Only Kane's verdict counts as proof. Never claim a flow passes without a Kane run.
- Never edit, delete or add files under `.gremlin/`, and never edit `gremlin.config.yaml`. Changing what is tested is never a fix; Gremlin reverts it.
- To turn a bug report into a test: `gremlin capture "<report>"`. To see open bugs: `gremlin bugs`.
<!-- gremlin:end -->
