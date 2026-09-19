# SmartPay — Nigerian payment app prototype

A working, installable prototype of a UPI-style Nigerian payment app: NIP transfers with account-name resolution, NQR scan-to-pay, bills and airtime, and an offline USSD fallback for when data drops mid-transfer.

**Live preview:** https://shekath.github.io/Smartpayment/

Open it on a phone and choose *Add to Home screen* (Chrome) or Share → *Add to Home Screen* (Safari). It installs with its own icon, launches full screen and works with no network.

## Flows you can walk through

- Withdraw to bank — NIBSS name enquiry, CBN Tier 2 limits, NIP fee bands and the ₦50 EMTL shown before you confirm
- Add money — bank transfer to your NIP virtual account, card top-up with fee shown before you commit, or a USSD string when there is no data
- Onboarding — phone entry with live carrier detection, OTP that auto-reads and self-verifies
- Home — balance, NIP virtual account with one-tap copy, live network state
- Scan — camera opens immediately, NQR detection, torch, My-code
- Send — contacts or 10-digit NUBAN with bank name resolution, amount keypad with balance guard, review, slide-to-send, PIN or fingerprint
- Offline USSD — tap the network pill on the home screen to cycle 4G → weak → no data, then send money. The transfer is intercepted and converted into a pre-filled USSD string.
- History — date-range filters (today, 7 days, 30 days, all time, or a custom range) plus type filters, with shareable receipts
- Account — security, notifications, cards and banks, help

## Deploying

The app is a static site: every file lives at the repository root and every asset
path is relative, so it runs unchanged from a GitHub Pages project URL.

Deployment is automated by `.github/workflows/pages.yml`, which uploads the
repository root as a Pages artifact and publishes it on every push.

One manual step is required before the first deploy can succeed. Creating a
Pages site needs repository admin rights, and the token a workflow runs with
does not have them, so the workflow cannot turn Pages on by itself:

1. Open **Settings → Pages**.
2. Under **Build and deployment**, set **Source** to **GitHub Actions**.

After that, re-run the latest *Deploy to GitHub Pages* job from the **Actions**
tab, or push any commit. The site appears at
https://shekath.github.io/Smartpayment/ about a minute later, and every later
push redeploys it with no further setup.

The push trigger lists both `main` and the current deployment branch, so the
site publishes before that branch is merged. Once `main` is the deployment
source, drop the extra branch from the trigger.

### Running it locally

No build step and no dependencies. Serve the folder over HTTP so that the
service worker and the web manifest load:

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000. Opening `index.html` straight from the
filesystem also renders the app, but the offline cache stays disabled.

## Build a native APK or IPA

This same `index.html` is the web bundle in the Capacitor build kit. Drop it into `www/` there and run `npm run apk:debug`.
