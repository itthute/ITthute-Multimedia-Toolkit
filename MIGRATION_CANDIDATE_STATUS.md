# ITthute Multimedia Toolkit alpha27 Migration Candidate

**Status:** approved source migration implemented and tested locally; complete Git source-tree import, APK build, signing and physical-device acceptance are still release gates.

## Approved candidate identity

- Product: **ITthute Multimedia Toolkit**
- Version: `2.0.0-alpha27`
- versionCode: `20026`
- Android package / Java package preserved: `za.co.itthute.fetchaudiovid`
- APK signer preserved: SHA-256 `9df337ed2d87f165b60352f8c1e81ae070ad3905a6c67a0a90f766f39025c7cf`

## Implemented migration controls

- Toolkit visible branding with legacy Android technical identity preserved.
- Legacy Fetch AudioVid storage roots remain discoverable; no destructive folder rename.
- Production date-PIN activation replaced by RSA/SHA-256 signed `IMT1` license tokens bound to a persistent app-instance ID.
- Existing alpha26 activation is honored only through its already-earned expiry.
- Fresh administrator access creates credentials; password verifier uses a random salt and PBKDF2 rather than a source-known shared default.
- Explicitly customized alpha26 administrator credentials can migrate once after successful legacy verification.
- Legacy update feed remains the alpha27 default while the future Toolkit feed identity is present for staged cutover.
- `sign-release.sh` repaired to fail closed on package, versionCode, versionName and retained signer.

## Verified local evidence

Persistent alpha27 local regression suite passes, including LicenseTokenPolicy, AdminCredentialPolicy, existing URL/cookie/clip/PDF/LinkedIn tests, Java syntax and source regression. A real offline licensing issuer -> embedded production public-key self-test also passes. The retained 2026-v2 PKCS#12 APK key was independently verified as a PrivateKeyEntry with the exact alpha26 certificate fingerprint.

## Durable source snapshot

A sanitized, non-release alpha27 migration work snapshot is archived in the ITthute Multimedia Toolkit Google Drive project root. Current snapshot SHA-256:

`f6eb9431007032bd0c397718851f3286d3b2134f422456b8fb72d553cea3a021`

Drive file ID: `1CaCnrm4zdp4ne6IUla_Ou5tKAiUwcJUA`
Checksum Drive file ID: `1s1JN4PLXDu9_zmu8yt2rV_dZ714gdPPA`

GitHub issue #1 tracks the complete sanitized alpha26/alpha27 source-tree import. The checkpoint/status commit is not a substitute for source synchronization.

This snapshot is **not a release** and must not be placed in the formal release-versions archive as a substitute for a built/signed/tested release.

## Remaining P0 gates

1. Import the complete sanitized source tree to this feature branch and record the exact Git commit.
2. Produce a clean unsigned alpha27 APK from that exact source commit.
3. Sign with the recovered retained APK key and verify package/version/signer/hash.
4. Samsung Galaxy S25 Ultra fresh-install and alpha26-to-alpha27 upgrade acceptance.
5. Production signed-license activation and administrator migration acceptance.
6. Facebook/Instagram/LinkedIn current-URL cookie state regression.
7. Live media download regression.
8. Disposable SAF/Pictures-to-PDF cleanup safety tests.
9. Publish and prove the backward-compatible update-feed transition.
10. Only then create the formal release package/checksum, archive to Drive versions, and review/merge to `main`.

Do not commit APK signing private material, licensing private material, passphrases, cookies, sessions, user diagnostics or private media.
