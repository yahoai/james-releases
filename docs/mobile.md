---
title: Remote & Mobile
order: 12
---

# Remote & Mobile

James runs on your Mac, but you can use it from your phone, a tablet or another computer. Your sessions keep running on the Mac while you're away.

The safe way to do this is [Tailscale](https://tailscale.com) — a free private network between your own devices. James never opens itself to the internet or your Wi-Fi.

## How James protects itself

Out of the box, James only accepts connections from the Mac it runs on. When you reach it through Tailscale, it also accepts requests from **devices signed in to your own Tailscale account** — no password or token needed. Everything else is refused:

- Devices on other people's Tailscale accounts, or devices shared into your tailnet
- Tagged devices (servers you tagged in the Tailscale admin console)
- Tailscale Funnel (public internet) traffic
- Anything on your local Wi-Fi

## Set up Tailscale (one time)

1. Install Tailscale on your Mac and on your phone, and sign in to **the same account** on both.
2. In the [Tailscale admin console](https://login.tailscale.com/admin/dns), turn on **MagicDNS** and **HTTPS Certificates**.
3. On the Mac, open Terminal and run:

   ```bash
   tailscale serve --bg --https=31010 31010
   ```

   If `tailscale` isn't found, use the full path to the app's CLI:

   ```bash
   /Applications/Tailscale.app/Contents/MacOS/Tailscale serve --bg --https=31010 31010
   ```

   This publishes James (which listens on port 31010) to your tailnet only, over HTTPS. The `--bg` flag keeps it running after you close Terminal and across restarts.

4. Run `tailscale serve status` to see your address. It looks like:

   ```
   https://my-mac.tail1234.ts.net:31010 (tailnet only)
   ```

You can also copy the address from the James status bar (bottom right) — click the copy icon next to it.

To stop sharing, run `tailscale serve --https=31010 off`.

## Open James on your phone

1. Make sure Tailscale is connected on the phone.
2. Open the `https://…ts.net:31010` address in Safari or Chrome.
3. That's it — you're in, with all your sessions.

### Install it as an app

Add James to your Home Screen for a full-screen app with its own icon:

- **iPhone / iPad:** in Safari, tap Share → **Add to Home Screen**.
- **Android:** in Chrome, tap ⋮ → **Install app** (or **Add to Home screen**).

Use the HTTPS address above. Voice input and push notifications only work over HTTPS.

### Push notifications

Go to **Settings → Notifications → Push** and turn on **Push to this device**. Use **Send test** to check it works.

You'll get a push for approvals, questions, todos waiting on you, failed job runs, and sessions that finish after a minute or more. To avoid buzzing you while you're at your desk, pushes are sent only while your most recent message came from a phone or tablet.

On iPhone, push only works when James is opened from the Home Screen icon.

### Mobile layout

On a phone, James uses bottom tabs: **Home**, **Todos**, **Sessions** and **More** (Jobs, Vault, Projects & sessions). The model, effort and permission controls are grouped under the **Mode** button next to the message box. Account usage is in the header menu.

## Use another Mac (Peers)

If you run James on more than one Mac, they can find each other over Tailscale.

1. Install James and Tailscale on each Mac, signed in to the same Tailscale account.
2. Run the `tailscale serve` command above on **each** Mac.
3. Open **Settings → Peers**. Other Macs appear under **Peers** within a minute. If one doesn't, add it under **Add peer manually** with its Tailscale IP (`100.x.y.z`) and port `31010`.

Once connected you can:

- **Start a session on another Mac** — pick it under **Machine** in the new session dialog (⌘K). The session runs on that Mac and streams to the one in front of you.
- **Move a session to another Mac** — session ⋮ menu → **Continue on another machine…**. James writes a handoff and opens a draft on the other Mac; you send it when you're ready.
- **Send a file or snippet** — **Send to peer…** on a message, code block or file. It lands in the other Mac's **Inbox** (status bar). Nothing runs automatically.

Update James to the same version on every Mac. A peer running a different version shows a warning badge.

## Troubleshooting

- **"Forbidden: requests are only accepted from this machine or your own Tailscale devices"** — the device isn't signed in to the same Tailscale account as the Mac, or it's a tagged device.
- **Page won't load** — check Tailscale is connected on both devices, and that `tailscale serve status` on the Mac still shows the 31010 entry. James must be running on the Mac.
- **"Microphone unavailable — An HTTPS connection is required"** — you opened an `http://` address. Use the `https://…ts.net` address.
- **Settings → Peers says "Not installed" / "Not running"** — install the Tailscale app on the Mac and sign in.
