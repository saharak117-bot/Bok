# Ad Blocker Android (prototype)

Android app prototype using `VpnService` to route DNS requests to a local virtual DNS endpoint and filter a small domain denylist. No root required.

## Build
1. Install Android Studio (Giraffe or newer) and Android SDK Platform 35.
2. Open this folder as a project.
3. Let Gradle sync, then Build > Build Bundle(s) / APK(s) > Build APK(s).
4. The debug APK is created at `app/build/outputs/apk/debug/app-debug.apk`.

## Important limitations
- This is a **prototype source project**, not a production-hardened DNS firewall.
- DNS/UDP IPv4 requests are handled; IPv6, TCP DNS, DoH/DoT, encrypted in-app DNS, and other bypass paths are not filtered.
- Only the small sample domain list in `AdBlockVpnService.kt` is blocked. Review and expand it responsibly.
- YouTube ads cannot be reliably removed by DNS filtering because ad delivery may share domains with video/content delivery.
- The current minimal app does not include a complete domain-list updater, custom-rule editor, persistent statistics UI, or battery/background optimization handling.
- If browsing or apps stop resolving names, stop the VPN from the app or Android VPN settings.

## Privacy
The app forwards unblocked DNS queries to Cloudflare DNS at `1.1.1.1`. This means the DNS provider can receive domain lookup requests. Change the upstream resolver in `forwardDns()` if desired.
