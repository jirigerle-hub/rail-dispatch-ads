# Android AdMob + GDPR Implementation Checklist

This checklist ensures consent withdrawal is handled correctly in the app (not only on the website).

## 1) Use Google UMP SDK in the app

- Integrate Google User Messaging Platform (UMP) SDK in the Android app.
- Request and update consent status at app start (before loading ads).
- Show consent form whenever required by UMP.

## 2) Store and respect current consent state

- Keep current consent state in app logic (from UMP APIs).
- Do not load personalized ads unless valid consent exists.
- If consent is denied or withdrawn, request only non-personalized ads.

## 3) Add a permanent in-app privacy entry

- Add a visible menu item in app settings: "Privacy & Ads".
- Include actions:
  - "Review privacy choices"
  - "Withdraw AdMob consent"
- This must be reachable at any time, not only on first launch.

## 4) Implement withdrawal flow

- On "Withdraw AdMob consent", reset/reopen consent flow via UMP.
- Let user explicitly choose new preference.
- Apply the new preference immediately for next ad requests.

## 5) Apply ad request mode correctly

- For withdrawn/denied consent, use non-personalized ad mode.
- Ensure mediation partners also receive correct consent signals.
- Avoid caching old ad request settings after consent change.

## 6) Handle external requests from website/email

- Requests from https://jirigerle-hub.github.io/rail-dispatch-ads/withdraw-consent.html go to app owner, not Google support.
- Define internal SLA (e.g. process within 30 days).
- Reply to user with confirmation and practical steps in app.

## 7) Add user-facing wording

- In app and policy, clearly state:
  - Consent can be changed anytime in app settings.
  - Withdrawal affects future ad processing.
  - Contact email for privacy rights requests.

## 8) Test scenarios before release

- Fresh install (EEA user): consent form appears before ads.
- Consent granted: personalized ads allowed.
- Consent denied/withdrawn: non-personalized ads only.
- User changes preference later: app updates behavior immediately.

## 9) Play Console / policy alignment

- Ensure Data safety form matches actual ad/consent behavior.
- Keep privacy policy links valid in store listing and app.
- Keep app-ads.txt up to date.

## 10) Minimal release acceptance criteria

- User can open "Privacy & Ads" anytime.
- User can withdraw AdMob consent in <= 3 taps.
- App stops personalized ad requests after withdrawal.
- Privacy request contact path works and is monitored.

---

## Suggested owner workflow for a website request

1. Receive request from the withdraw-consent page.
2. Confirm receipt by email.
3. Ask user to update consent in app via "Privacy & Ads".
4. If needed, provide troubleshooting steps/screenshots.
5. Confirm closure.

This process is required because Google does not automatically process your app user's consent withdrawal from your website form alone.
