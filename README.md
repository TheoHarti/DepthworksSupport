# Depthworks support

Support page for Depthworks app, published by FindusLab.

The static site in `docs/` contains the support page and the privacy policy for
AdMob, Google Play, Apple's App Store, and the in-game settings link. It uses
plain HTML and CSS: no build step, JavaScript, analytics, ads, remote fonts, or
cookie banner is needed for the site's own content.

## Publish with GitHub Pages

1. Commit and push the site files to `main` in this repository.
2. On GitHub, open **Settings → Pages**.
3. Under **Build and deployment**, select **Deploy from a branch**.
4. Choose **main** and **/docs**, then **Save**.
5. Wait for the Pages deployment to finish and check both public URLs below.

GitHub Pages serves this public repository over HTTPS. Future pushes to `main`
update the site automatically. `docs/.nojekyll` keeps it a plain static site.

| Where to use it | URL after publishing |
| --- | --- |
| AdMob privacy policy, both apps | https://theoharti.github.io/DepthworksSupport/privacy/ |
| Google Play privacy policy | https://theoharti.github.io/DepthworksSupport/privacy/ |
| App Store privacy policy | https://theoharti.github.io/DepthworksSupport/privacy/ |
| App Store support URL / general support | https://theoharti.github.io/DepthworksSupport/ |

The app's **Settings → Privacy policy** opens the same privacy URL. The policy
must be publicly accessible before publishing the AdMob consent message or
submitting the app to a store. Store Data safety / App Privacy questionnaires are
separate submissions; the policy URL does not fill them out automatically.

## AdMob app-ads.txt

`docs/app-ads.txt` authorizes Google's ad exchange for the AdMob publisher used
by both the Android and iOS apps:

```text
google.com, pub-2111037597422722, DIRECT, f08c47fec0942fa0
```

This repository's Pages deployment publishes it at
https://theoharti.github.io/DepthworksSupport/app-ads.txt. AdMob checks the root
of the developer website's hostname, so it needs the same file at
https://theoharti.github.io/app-ads.txt.

The root URL is served by a separate public GitHub Pages repository named
`TheoHarti/theoharti.github.io`. A ready-to-publish checkout is prepared in
`C:\Projects\Private\theoharti.github.io`, containing the same `app-ads.txt` and
a home page that directs visitors to this support site. Publish that repository
using **Settings → Pages → Deploy from a branch → main → /(root)**. Keep both
copies of `app-ads.txt` in sync if the publisher or authorized ad networks change.
The privacy policy and support URLs above continue to use this repository.

For store verification, use the support URL as the developer website in Google
Play and the marketing URL in App Store Connect. After linking the published
store entries in AdMob, use **Apps → View all apps → app-ads.txt → Check for
updates**, then complete app verification. The file authorizes mobile app ads;
the support website itself does not display ads.

References:

- [Google: set up app-ads.txt](https://support.google.com/admob/answer/9363762?hl=en)
- [Google: verify an app](https://support.google.com/admob/answer/14538460?hl=en)
- [GitHub Pages user sites](https://docs.github.com/en/pages/quickstart)

## Maintain the policy

- Developer/controller: **Theodor Hartleitner, operating as FindusLab**, Austria.
- Public support/privacy email: **findus.lab@gmail.com**.
- Intended audience: general audience, not specifically directed at children.
- Policy text: `docs/privacy/index.html`; update the date when changing it.
- Shared appearance: `docs/styles.css`; support copy: `docs/index.html`.
- Keep the policy synchronized with the app's actual SDKs, services, permissions,
  support practices, and advertising configuration. Review any new mediation
  partners before enabling them.
- Confirm the store audience/age settings match the intended audience and that
  native consent controls work on a device before release. iOS tracking, if
  introduced, needs its own review and required platform permissions.

## Basis for the current disclosures

The October 2026 policy was written against the app's current implementation:

- `GameSaveRepository` and the save platform implementations keep saves,
  preferences, and recovery snapshots locally. Reset keeps preferences; operating
  system backups are separate.
- `DepthworksGame.onLoad` starts progression/performance telemetry only in debug
  builds. Logs remain local and are exported only by user action.
- `AdMobRewardedAdService` uses Google Mobile Ads and UMP on Android/iOS, with
  consent checks in release/profile builds and a privacy options entry where
  required. There is no separate Firebase Analytics, crash-reporting, account, or
  developer-hosted backend in the current app.
- No precise location, camera, microphone, contacts, or photo access is requested.
- The static support site has no third-party embeds or client-side trackers;
  GitHub Pages still processes technical hosting requests.

Primary references for updating these disclosures:

- [Google Mobile Ads: Android data disclosure](https://developers.google.com/admob/android/privacy/play-data-disclosure)
- [Google Mobile Ads: iOS data disclosure](https://developers.google.com/admob/ios/privacy/data-disclosure)
- [Google Play: user data and privacy policy requirements](https://support.google.com/googleplay/android-developer/answer/10144311)
- [Apple: App Review Guidelines, privacy](https://developer.apple.com/app-store/review/guidelines/#privacy)
- [GitHub Privacy Statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement)
- [GitHub Pages publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

