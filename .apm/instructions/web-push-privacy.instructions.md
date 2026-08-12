---
applyTo: "**/push*,**/push*/**,**/sw*,**/service-worker*,**/service-worker*/**,**/notification*,**/web-push*"
description: "Harness Rule: Web Push — no broadcast; preference gates; purge gone endpoints; no push signing secrets in git"
harnessRule: web-push-privacy
source: okf/harness-rules/web-push-privacy.md
---

# Harness Rule: Web Push Privacy

No broadcast-to-all push. Send per user with enabled prefs + subscription. Separate preference categories. Delete 404/410 endpoints. Never commit push signing / private secrets. Include push data in export/delete paths.

Source: `okf/harness-rules/web-push-privacy.md`
