---
layout: default
title: MeetMi Support
---

# MeetMi Support

Version: `managed-ai-apple-pages-v1`<br>
Applies to MeetMi Managed AI on the Mac App Store.

[中文](../zh/support/) · [Privacy Policy](../privacy/)

## Contact

After the Apple Developer Program account is opened, this page will list the public support email and expected response time. Until then, treat this page as the review and product draft.

Do not send API keys, license keys, JWTs, transaction JWS, or meeting transcripts in support mail.

## What MeetMi does

MeetMi transcribes a meeting on the device and, after consent, sends transcript text, questions, and relevant workspace snippets through MeetMi relay → OpenRouter → listed ZDR providers. Raw audio is not saved or uploaded. Speech recognition and translation stay on the device.

Version 1 is one monthly subscription. There is no Credit top-up. Exhausted credit or an unavailable entitlement stops new AI requests only; local transcription, translation, history, and export continue.

## Purchases and subscriptions

1. Open Settings → Apple Service.
2. Buy the monthly MeetMi Managed AI subscription, or use Restore Purchases.
3. Manage or cancel the subscription in Apple Account / App Store subscription settings. MeetMi cannot cancel an Apple subscription itself.

If a purchase is pending family approval, local meeting features remain available. Refunds and revocations are processed by Apple and then reflected in MeetMi entitlement.

## Permissions

- Microphone: capture the user's speech after a meeting starts.
- Screen and system audio on macOS: capture the other side of a meeting app. Raw audio is not stored.
- User-selected folder: read workspace documents and write meeting notes. The sandboxed Mac app uses a security-scoped bookmark. If the folder moves or permission is withdrawn, choose the folder again.

System permission is not consent from other participants. The user must give any notice required by law or workplace policy.

## Meetings, workspaces, and notes

- A meeting does not start until the user presses start.
- Pause stops capture and automatic AI; ending a meeting can still generate notes because that is an explicit action.
- Notes are written to the workspace `Meetings` folder, or to Documents/Meetings when no workspace is selected.
- Removing a workspace only forgets it in the app. It does not delete the folder.

## AI, credit, and network failures

- Cloud AI requires an active subscription, remaining credit, and accepted data notice.
- Withdrawal of cloud-AI consent stops new cloud sends.
- Credit remaining, included period allowance, and purchased credit are shown separately. Version 1 does not sell purchased credit.
- Meeting-time estimates are not a store promise.
- Relay, OpenRouter, or provider failures stop AI only.

## Deleting data

- Delete meeting history in the app.
- Clear rebuildable caches and debug logs in Settings.
- Delete workspace files in Finder.
- Uninstalling the app does not delete a user-selected workspace.
- Server-side entitlement/usage deletion can be requested after launch through the published support contact.

## Known limits

- macOS 26 or later.
- iOS Managed is not in the first store release.
- Mainland China is excluded until a separate legal assessment is complete.
- Simulator builds cannot run on-device speech models.
- GitHub Pages URLs become publicly reachable only after stage 9 enables Pages.

## Review path

Reviewers can buy or restore the Sandbox monthly product, accept or decline cloud AI, choose a folder, start a meeting, pause, end, and confirm that notes are written back. No API key, JSON file, or command line is required.
