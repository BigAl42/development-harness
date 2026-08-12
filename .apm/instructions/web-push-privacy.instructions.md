---
applyTo: "**/push*,**/push*/**,**/sw*,**/service-worker*,**/service-worker*/**,**/whats-new*,**/notification*"
description: "Harness Rule: Web Push — no broadcast; preference gates; purge gone endpoints; no VAPID secrets in git"
harnessRule: web-push-privacy
source: okf/harness-rules/web-push-privacy.md
---

# Harness Rule: Web Push Privacy

No broadcast-to-all push. Send per user with enabled prefs + subscription. Separate preference categories. Delete 404/410 endpoints. Never commit VAPID/private secrets. Include push data in export/delete paths.

Source: `okf/harness-rules/web-push-privacy.md`
