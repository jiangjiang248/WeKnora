# WeKnora #4520 routing verification

These screenshots are generated from an isolated browser regression fixture with the actual `handleClose` extracted from `Settings.vue` and real Vue Router 4.5.0.

They are not screenshots of the full application or a deployed-backend end-to-end test.

- Baseline source: Tencent/WeKnora commit `968ca9fb1b7dab6f96dcbf3ee7e4c330abca253f`.
- Browser: headless Microsoft Edge 155.0.4283.62.
- Before: direct entry to settings after a page outside `/platform/`, then close, returns to that outside page.
- After: the same action navigates to `/platform/knowledge-bases`.
- Additional assertions: direct entry with native history length 4 remains in the app; normal Vue Router in-app back navigation is preserved.
- The fixture uses no backend, account data, credentials, or model calls.

The code PR changes only `Settings.vue` and its existing navigation test file. This evidence branch is separate and is not proposed for merging upstream.
