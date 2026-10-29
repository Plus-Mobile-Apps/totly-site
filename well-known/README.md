# App-association files (`.well-known`)

These tie the native Totly apps to `totly.plusmobileapps.com` so the OS password
managers offer credentials saved for the website inside the app (and vice-versa)
when signing in.

They **cannot** live in `docs/` — MkDocs silently drops any dot-prefixed path.
Instead the deploy workflow (`.github/workflows/deploy.yml`) copies them into the
built `site/.well-known/` and publishes with `.nojekyll` so GitHub Pages doesn't
strip the dot-directory. Edit them here; the workflow does the rest on push to
`main`.

## Files

| File | Platform | Served at |
|------|----------|-----------|
| `assetlinks.json` | Android | `https://totly.plusmobileapps.com/.well-known/assetlinks.json` |
| `apple-app-site-association` | iOS (no extension) | `https://totly.plusmobileapps.com/.well-known/apple-app-site-association` |

- **`assetlinks.json`** — `get_login_creds` and `handle_all_urls` for package
  `com.plusmobileapps.totly`.
- **`apple-app-site-association`** — a `webcredentials` section for
  `Y89258SF5P.com.plusmobileapps.totly.Totly` (`Y89258SF5P` is the Team ID), and the `applinks`
  section described below.

## Android signing fingerprint

`assetlinks.json` still has a `TODO_REPLACE_WITH_PLAY_APP_SIGNING_SHA256`
placeholder. Replace it with the SHA-256 of the certificate that signs the
**installed** app:

- **Play App Signing (production):** Play Console → your app → *Test and release*
  → *App integrity* → *App signing* → the **App signing key certificate** SHA-256.
- **Local/debug testing:** `keytool -list -v -keystore ~/.android/debug.keystore
  -alias androiddebugkey -storepass android` and add that SHA-256 too.

Multiple fingerprints are allowed — it's a JSON array.

## App-side counterparts (in the `totly` repo, not here)

- **iOS** — a `com.apple.developer.associated-domains` entitlement with
  `webcredentials:totly.plusmobileapps.com`. Without it iOS never fetches the
  AASA file.
- **Android** — autofill needs nothing beyond the field hints.

## App links: `/invite/`

The family invite email links to `https://totly.plusmobileapps.com/invite/`. With the app installed
iOS and Android open More › Notifications in the app instead; otherwise the link shows
[`docs/invite.md`](../docs/invite.md), with store badges and a `totly://notifications` button.

- **`apple-app-site-association`** — an `applinks` section matching `/invite` and `/invite/*` for
  the same app ID. The app needs the `applinks:totly.plusmobileapps.com` associated domain.
- **`assetlinks.json`** — the `delegate_permission/common.handle_all_urls` relation on the same
  statement. The app has an `https` `VIEW` intent filter with `android:autoVerify="true"` for the
  `/invite` path. Android only opens the link in the app once the fingerprint above is real.

To open more paths in the app, add them to both the AASA `components` and the Android intent filter.

## Verify after deploy

```bash
curl -i https://totly.plusmobileapps.com/.well-known/assetlinks.json
curl -i https://app-site-association.cdn-apple.com/a/v1/totly.plusmobileapps.com
```

Both endpoints must be HTTPS with **no redirects**, so turn on *Enforce HTTPS* in
the repo's Pages settings.
