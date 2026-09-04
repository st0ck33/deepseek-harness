# Changelog

## 0.1.2-rc.1 (unreleased)
### Added
- `SessionEnd` is now a supported, observe-only hook event. The harness has no
  dedicated session-end lifecycle event for the agent loop, so the bridge emits it
  from `agent/disposed` — once when an agent's owning fiber is torn down (i.e. when
  the conversation/session ends). It runs detached and cannot block or add context.
  The payload carries `session_id`, `cwd`, `hook_event_name: "SessionEnd"`, and
  `stop_hook_active: false` (`transcript_path` stays empty).
- `sessionEndPayload(agent)` mirrors `stopPayload`.
- A `SessionEnd` command hook configured in `hooks.json` is now parsed and
  registered instead of being skipped as unsupported.
