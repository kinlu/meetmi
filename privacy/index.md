---
layout: default
title: MeetMi Privacy Policy
---

# MeetMi Privacy Policy

Version: `managed-ai-apple-pages-v3`<br>
Effective: 2026-09-26 (v2: 2026-09-19, v1: 2026-08-29)<br>
Applies to: MeetMi Managed AI distributed through the Apple App Store on macOS and iPhone. Both apps are one App Store record with one shared subscription and use this same policy.

Developer / legal entity, postal address, and privacy contact will be filled when the Apple Developer Program account is opened. Until then this page is the canonical draft that App and store materials must match.

[中文](../zh/privacy/) · [Support](../support/)

## 1. Scope

This policy applies to MeetMi Managed AI sold through the Apple App Store.

MeetMi Local is a separate BYOK product with a different app identity, storage, preferences, logs, and Keychain service. It uses the user's API key to connect directly to a user-selected OpenRouter or HTTPS Responses endpoint. Local does not use the MeetMi relay, subscription entitlement, or Credit system.

## 2. On-device processing

- The microphone and, on macOS, system audio are used only after the user starts a meeting.
- MeetMi does not save or upload raw audio.
- Speech recognition and subtitle translation use Apple on-device capabilities.
- Transcripts, advice, analysis, notes, workspace indexes, and extraction caches are stored on the device or in a user-selected workspace by default.
- On iPhone the microphone is the default and the only audio source on iOS 26. From version 1.0.1 on iOS 27, the user may instead choose system audio: at the start of each meeting iOS shows its own sharing sheet, and once the user agrees MeetMi receives the sound the phone is playing (a video, a lecture, a podcast). Only the sound is used; screen frames are discarded as they arrive and are never stored or uploaded. iOS does not pass call audio (phone, FaceTime, WeChat, Zoom and similar) to any app, so calls cannot be heard this way. A meeting the user has started keeps transcribing while the phone is locked or another app is in front; it stops when the user ends or pauses it.

## 3. Managed cloud AI

After explicit consent, MeetMi may send the on-device transcript, user questions and stated concerns, existing analysis, task context, relevant workspace snippets requested by AI, and protocol data needed for strict tools and structured output.

Recipient chain:

```text
MeetMi (App Store, macOS or iPhone) → MeetMi relay → OpenRouter → the ZDR model providers listed in the active in-app policy
```

Current in-app policy names DeepSeek V4 Flash and the ZDR provider range DigitalOcean, Morph, CoreWeave, and Together. The relay does not intentionally persist or log transcripts, questions, document snippets, request bodies, upstream error bodies, or streamed response content. Content is nevertheless processed transiently in relay memory and by OpenRouter and the upstream provider for routing and inference. Upstream services see the relay network address rather than a direct connection from the user's device.

Before sending, the app displays the relay domain, model, ZDR provider range, data scope, and policy version. A material change to recipients, model, providers, scope, or policy invalidates prior consent and requires renewed consent.

## 4. Web search

Web search is **off by default**, is stored as its own consent record separate from the recording notice and Managed AI consent, and can be withdrawn on its own. It is used only by Deep Research and MeetMi discussions; **realtime advice and meeting notes never go online, and that is enforced on the server**, not merely by a setting in the app.

**Provider and domain.** The search provider is **Exa** (`api.exa.ai`). Requests are forwarded by the MeetMi relay, so Exa sees the relay's network address rather than a direct connection from the user's device. This path is separate from the AI inference chain and does not pass through OpenRouter.

**What is sent.** Only the **search terms** the model distils from meeting content. When the original text is needed, the **result URL** is also sent and Exa fetches the page. The full transcript, workspace documents, and the user's own questions are not sent to Exa.

**Retention and training.** Exa's published terms state that search terms sent to it may be retained and used to improve and train its own models. **This differs from cloud AI**, which runs over a server-enforced zero-retention (ZDR) route; web search does not. Search terms are distilled from meeting content and may contain company names, personal names, and other proper nouns mentioned in the meeting. The user must **explicitly acknowledge this when first enabling web search** before the feature becomes active. Exa's terms: <https://exa.ai/privacy-policy>.

**International processing.** Exa is a US provider and requests are processed on its servers.

**Renewed consent.** A change to the search provider, its domain, or the web-search policy version invalidates existing web-search consent and requires a fresh acknowledgement. Such a change does not affect the recording notice or Managed AI consent.

**Availability.** The App Store build connects to the production relay, so web search is available in it. It is off by default and stays off until the user turns it on and acknowledges the retention notice above.

## 5. Apple purchases, entitlement, and Credit

- Purchases and subscriptions are processed through Apple StoreKit and the App Store. MeetMi does not process full card details in the app.
- Necessary StoreKit transaction JWS data and an opaque association value may be sent to the MeetMi relay to validate subscription, refund, revocation, and restoration and to issue a short-lived access token.
- JWTs contain no Apple ID, email, full transaction JWS, or OpenRouter key.
- The service stores entitlement, Credit, and content-free usage against an opaque subject.
- Version 1 is one monthly subscription with Managed AI allowance that resets with the subscription period. The subscription is a universal purchase: one subscription covers the Mac and iPhone apps, and the allowance is one pool shared by both.
- Version 1 does not sell Credit top-ups. If consumable IAP Credit is introduced later, it will be accounted for separately from monthly allowance and will not expire merely because a monthly period resets.
- If entitlement or Credit is unavailable, new AI requests stop while on-device transcription, translation, history, and export continue.

## 6. Credit metering

The technical baseline meters `input tokens + 2 × output tokens` and converts that amount to Credit. Content-free usage is recorded by activity: meeting listening, user questions, deep research, advisor discussion, and meeting notes.

The app may show Credit, period reset, activity breakdown, and a settings-based meeting-time estimate. The estimate is not a guarantee. MeetMi Local does not use Credit.

## 7. Local logs and caches

Detailed debug logging is off by default. When enabled it may contain meeting content, prompts, and diagnostics, but authentication headers, Apple transaction credentials, JWTs, licenses, API keys, and cookies are excluded or redacted.

Users can clear logs and rebuildable document caches. Production relay configuration disables request-content observability and does not use Tail, Logpush, Sentry, or another service to log meeting content.

## 8. Controls and deletion

Users can decline or withdraw Managed AI consent, disable or withdraw web-search consent, use Apple's subscription management and restore-purchase features, delete meeting history, clear caches and logs, and delete files in their own workspaces.

Removing the app may not remove files in a user-selected workspace. Those files are managed by the user in Finder (macOS) or the Files app (iPhone). A request to delete server-side entitlement or usage records is separate from deleting local or workspace files; use the Support page after launch.

## 9. Third parties, international processing, and security

Apple, OpenRouter, providers listed in the active policy, and — once the user separately consents to web search — the search provider Exa may process relevant data outside the user's country under their own policies. Before launch, MeetMi will link the final OpenRouter and provider terms, retention/training statements, and any applicable DPA. Providers that cannot be confirmed will not be in the launch allowlist.

Upstream providers on the AI inference route are bound by ZDR and `data_collection: deny`. **Web search is not on that route and does not carry the same guarantee** — see section 4.

Controls include a strict request allowlist, a ZDR provider allowlist, `store=false`, price limits, short-lived JWTs, separate Keychain storage, App Sandbox, encrypted transport, and content-logging prohibitions. No internet transmission can be guaranteed absolutely secure.

OpenRouter privacy information: [https://openrouter.ai/privacy](https://openrouter.ai/privacy)

Exa privacy information: [https://exa.ai/privacy-policy](https://exa.ai/privacy-policy)

## 10. Recording and user responsibility

Meetings may contain another person's personal information, confidential information, or regulated data. The user is responsible for notices, permissions, and authority required by applicable law, contract, organisational policy, and meeting rules.

System microphone/screen-recording permission, MeetMi's recording notice, and Managed AI consent are not consent from other participants.

## 11. Children, tracking, and sale

MeetMi is not directed to children, does not perform cross-app tracking, does not sell personal information, and does not use meeting content for advertising.

## 12. Regional availability

Mainland China is excluded from the first release until a separate PIPL and filing assessment is complete. Other regions will be reviewed for recording, privacy, consumer, and transfer rules before the store record is submitted.

## 13. Changes and contact

Updates will identify a version and effective date. Material changes to cloud-AI recipients, data scope, purchasing, or retention will also trigger renewed in-app consent or an updated notice.

- Privacy contact: to be published with the Apple Developer Program legal entity
- Support: [Support page](../support/)
- Public Privacy URL: `https://kinlu.github.io/meetmi/privacy/`
