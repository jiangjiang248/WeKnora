# WeKnora issue #4608 browser regression evidence

Issue: https://github.com/Tencent/WeKnora/issues/4608

Baseline: 92dfa6a1eef2be18df81c2b5fe23bc43e6f3783e

Fix: 98d7c6c850e5d6ce7936d8995a19e244986234d8

Captured on 2026-10-22 Asia/Shanghai with Ego Lite. Actual KnowledgeBase.vue setup/handlers were compiled from each source version and mounted with Vue. APIs and surrounding stores were mocked; the list display was simplified. This is an isolated component/browser regression, not a full application deployment, real rebuild backend, or model integration test.

Both runs start with 70 loaded document rows. The mocked first-page list endpoint returns 35 rows. The same real confirmBatchReparse handler rebuilds Document 70.

| Observation | Before | After |
| --- | ---: | ---: |
| Whole-list reloads | 30 | 0 |
| Retained loaded rows | 35 | 70 |
| Targeted row-status requests | 0 | 2 |
| List loading transitions | 60 | 0 |

The fixed row reaches completed. The production row-poller and 12-second acknowledgement boundary are additionally covered by the repository regression tests.

The evidence-only branch adds this README and two unedited native browser screenshots. These files are not part of the source-fix PR.
