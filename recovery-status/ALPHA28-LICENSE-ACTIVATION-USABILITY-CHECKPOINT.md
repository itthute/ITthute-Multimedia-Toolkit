# ITthute Multimedia Toolkit — alpha28 activation usability checkpoint

Status date: 2026-08-19 SAST

This is a truthful checkpoint record for the alpha28 working candidate. It is **not** a claim that the complete alpha28 source tree has been synchronized to GitHub. Full sanitized source-tree import remains tracked by GitHub issue #1.

## Candidate identity

- Product: ITthute Multimedia Toolkit
- Version name: `2.0.0-alpha28`
- Version code: `20027`
- Android package/application ID: `za.co.itthute.fetchaudiovid`
- IMT1 protocol: current `version=1` cryptographic contract retained
- Proposed commercial IMT1 payload v2/tier/seat design: **design only, not implemented in alpha28**

## Implemented alpha28 activation usability changes

- Scrollable activation-required UI.
- Browse/load a signed IMT1 token from a text file using Android's document picker.
- One-tap paste of a copied token from the clipboard.
- Administrator-configurable licensing/support email; packaged default `information@ITthute.Africa`.
- Administrator-configurable HTTPS product/licensing information URL; packaged default `https://ITthute.Africa`.
- Clickable licensing email and website on the activation gate.
- Prepared new-purchase or renewal email request with the current License instance ID, app version and configured website.
- License purchase/renewal Help and About accessible before activation.
- Help contains detailed purchase, renewal and token-loading steps.
- Activation, Help, About and Diagnostics consume the same validated configured contact values.
- Token file input is bounded to 64 KiB, text-only, rejects NUL/binary content, embedded whitespace and malformed three-part IMT1 candidates.
- Browsing/loading/pasting input does **not** consume an activation attempt. The counter changes only after the user taps Activate and the canonical verifier/policy engine rejects the candidate.

## Source/test status

A local reviewed alpha28 working tree exists outside GitHub pending full-tree synchronization. A new pure-Java `LicenseActivationPolicy` helper isolates contact/token-file validation from Android UI code.

Persistent local regression suite: **PASS**

- LicensePolicyTest
- LicenseTokenPolicyTest
- AdminCredentialPolicyTest
- LicenseActivationPolicyTest
- ActivationScenarioTest
- MediaUrlPolicyTest
- CookieFilePolicyTest
- ClipRangeRulesTest
- PostPictureSupportTest
- PicturePdfSupportTest
- LinkedInVideoSupportTest
- LinkedInFallbackBehaviorTest
- JavaSyntaxCheck (28 files)
- source_regression_test
- Full Android Java compilation/build

## Build/signing evidence

Unsigned APK SHA-256:
`a721c0b1dffc659f90807b911824d14b86ad8999e6436482afe42783443917bf`

Final signed candidate APK SHA-256:
`d690e8af9db212d47cbdae5ae26940e89ba0b3b246dc3c476b4d4163451fe42d`

Retained APK signer certificate SHA-256:
`9df337ed2d87f165b60352f8c1e81ae070ad3905a6c67a0a90f766f39025c7cf`

- ZIP alignment: PASS
- APK Signature Scheme v2: enabled
- APK Signature Scheme v1/v3/v3.1/v4: disabled
- Signer count: 1
- Signer continuity with alpha27: PASS

No APK signing private key, APK signing password, IMT1 private licensing key, licensing passphrase, cookies or private user media are contained in this checkpoint.

## Documentation synchronization

The permanent Google Docs for architecture, APK signing, installation/user guide, cross-platform development prompt, licensing procedure, licensing standard architecture, reusable licensing-development prompt and commercial/licensing matrix were updated in place for alpha28. The live project-management Sheet was also synchronized.

## Remaining formal-release gates

- Physical-device fresh install/upgrade acceptance on the Samsung Galaxy S25 Ultra.
- Browse/load token file UX acceptance.
- Clipboard paste UX acceptance.
- New-purchase and renewal email intent acceptance.
- Administrator support-email/HTTPS-URL configuration acceptance.
- Help/About activation-gate acceptance.
- Attempt-count semantics acceptance.
- Real signed-token/admin migration acceptance.
- Existing P0 cookie, PDF cleanup and representative media regressions.
- Backward-compatible update-feed acceptance.
- Complete sanitized source-tree Git synchronization and exact build-commit traceability.

Do not merge to `main`, archive a formal release ZIP, or describe alpha28 as released until the applicable gates above pass.