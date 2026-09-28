# 📡 SuperPinger — Network Tools & Monitoring

**Understand your connection. Monitor your hosts. Keep your network under control.**

SuperPinger is an Android toolkit for network diagnostics, live traffic monitoring, and host availability checks. Troubleshoot your Wi-Fi, check remote servers, and investigate connection issues from your phone.

## 📲 Download

### [Get SuperPinger on Google Play](https://play.google.com/store/apps/details?id=com.superpinger)

> This README describes the 1.8 feature set. Availability in the store depends on the published release.

## ✨ What's New

- 🤖 Telegram bot alerts when favorite hosts stop responding or recover.
- 📊 Live download and upload graphs for Wi-Fi and mobile data.
- 📱 Traffic widgets with an optional compact mode.
- 🔎 Extended TCP, DNS, IPv4, IPv6, and HTTPS diagnostics.
- 📈 Network quality history.
- ⚖️ Before-and-after session comparisons.
- 📤 Support reports with a summary and latency graph.
- ⭐ Customizable home screen shortcuts.
- ⏱️ Monitoring stop timers.
- 🔕 Eight-hour quiet mode.

## 🧰 Network Tools

| Tool | Features |
| --- | --- |
| 🎯 Ping | Response times, packet loss, live graphs, and configurable test settings |
| 🛤️ Traceroute | Route investigation with available hop addresses and response times |
| 📶 Network Scanner | Discovery of responding devices on the local network |
| 🌐 DNS Lookup | DNS record queries and domain resolution |
| 🚪 Port Scanner | TCP port availability checks |
| 📋 WHOIS Lookup | Available registration information for domains and IP addresses |
| ⭐ Favorites | Saved hosts for quick checks and background monitoring |
| 🕘 History | Previous results and data export |

## 📊 Live Traffic Monitoring

Watch your device's download and upload activity over Wi-Fi or mobile data.

- Real-time download and upload speeds.
- A graph of recent traffic activity.
- Daily and monthly data usage.
- Separate Wi-Fi and mobile traffic totals.
- A configurable mobile data limit with an alert.

Historical traffic totals require access to Android usage statistics. Mobile usage availability depends on the Android version and device.

## 📱 Home Screen Widgets

Keep network activity visible without opening the app.

- Download and upload speeds.
- A recent traffic graph.
- Compact mode without the graph.
- Light, dark, and system appearance.
- Configurable colors and update intervals.
- Widget preview in **More**.
- Quick Settings tile for monitoring control.

Enable traffic monitoring from **More** and confirm the battery-use warning. Appearance settings apply to all traffic widget instances.

## 🤖 Telegram Bot Alerts

Connect your own Telegram bot and receive favorite-host availability updates in your group.

### Setup

1. Create a bot using **@BotFather** in Telegram.
2. Add the bot to your group and allow it to send messages.
3. Open **More → Telegram Bot**.
4. Enter the bot token and numeric group chat ID.
5. Enable event delivery and save the settings.
6. Send a test message.
7. Add hosts to **Favorites** and enable host monitoring.

### Alert Behavior

- Two matching checks confirm an unavailable or recovered state.
- The initial successful state does not generate an alert.
- Losing internet access on the phone does not mark every host as offline.
- Pending events can be retried after temporary delivery failures.
- Quiet mode sends Telegram messages without notification sound.

The bot token is encrypted using **Android Keystore** and is excluded from application reports.

> Alerts depend on the configured interval and Android background restrictions. Delivery may be delayed, and network failures can occasionally cause duplicate messages. Host names and addresses are shared with the configured Telegram group.

## 🔎 Extended Diagnostics

### 🚦 Quick Connection Check

Check the local gateway, an external TCP endpoint, DNS, and HTTPS. Review response times and possible explanations for connection problems.

### 🚪 Custom TCP Port

Test a port of your choice or configure a TCP port in a diagnostic profile.

### 🌍 IPv4 and IPv6

Inspect connection results separately for the addresses returned by DNS and see when an address family is unavailable.

### 🧭 DNS Comparison

Compare system DNS results with **Google** and **Cloudflare DNS over HTTPS**, including A/AAAA records and request timings.

> DoH timings include HTTPS overhead, while system DNS may return cached results. These measurements are not a direct ranking of DNS server speed.

### 🔐 HTTPS and TLS

Inspect:

- HTTP response status.
- Request duration.
- TLS certificate expiry.
- Estimated days until certificate expiration.

HTTPS checks validate certificates and do not bypass TLS errors.

## 📈 Stability Monitoring

Create profiles for **Home**, **Work**, **Gaming**, or your own servers.

- Monitor up to five hosts in a diagnostic session.
- Choose ICMP, TCP, or automatic fallback.
- Review minimum, average, and maximum latency.
- Track packet loss and jitter.
- Measure observed periods without successful replies.
- Configure alert thresholds and cooldowns.
- Review network changes and session events.

Quality history groups results by profile name, network type, host, and measurement method. Use separate profile names to distinguish locations such as home and work.

## 📁 Reports & Comparisons

- Export session summaries and measurement data.
- Save CSV data for further analysis.
- Compare saved sessions before and after a network change.
- Review differences in latency, loss, jitter, and observed outages.
- Generate a support ZIP containing a text summary and PNG latency graph.

Reports are shared through Android's share menu when you choose to export them.

## ⚙️ Personalization & Controls

- 🌙 Light, dark, and system themes.
- ⭐ Favorite diagnostic tools on the home screen.
- ⏱️ Stop timers from **1 to 1,440 minutes**, or manual stopping.
- 🔕 Eight-hour quiet mode with an option to resume alerts.
- 🔔 Persistent monitoring notifications with stop controls.
- 🔋 Battery-use warnings before enabling background monitoring.

Timer settings apply to the next monitoring, diagnostic, or traffic-widget session.

## 🔒 Data & Permissions

History, profiles, and reports are stored on the device. Network checks contact the selected hosts and services. Enabling Telegram alerts sends configured monitoring events to Telegram.

| Permission or Access | Purpose |
| --- | --- |
| Notifications | Monitoring alerts, traffic-limit warnings, and service controls |
| Usage access | Daily and monthly device traffic statistics |
| Location permission | Connected Wi-Fi network name where required by Android |
| Phone state | Mobile network type and available signal information |

The application does not use GPS to track your movements.

Advertising SDKs may process data according to their privacy policies:

- **Google Play edition:** Google AdMob.
- **Separate RuStore edition:** Yandex Mobile Ads.

## ℹ️ Understanding the Results

- A missed ping does not necessarily mean a server is offline: some hosts block ICMP.
- A closed TCP port does not prove that the internet connection is broken.
- Automatic fallback can combine results from different test methods.
- Android battery optimization and device sleep can delay background checks.
- Background monitoring can increase battery consumption.
- SuperPinger helps diagnose connection problems; it does not increase internet speed.

For meaningful comparisons, use the same hosts, methods, ports, and similar test durations.

## 🛠️ Build from Source

The prepared 1.8 source projects use:

| Component | Version |
| --- | --- |
| Language | Kotlin |
| Minimum Android version | Android 7.0 / API 24 |
| Compile and target SDK | 36 |
| Android Gradle Plugin | 9.0.1 |
| Gradle | 9.1.0 |
| Gradle JDK | 21 |

Open the project in a compatible Android Studio version, configure the Android SDK, and sync Gradle.

### Verify Without Packaging an APK

```bash
./gradlew :app:compileDebugKotlin :app:compileReleaseKotlin :app:testDebugUnitTest :app:lintDebug
```

### Windows

```powershell
.\verify_sources.bat
```

### Include Release Optimization with R8

```powershell
.\verify_optimized_sources.bat
```

Use your own signing configuration when preparing a release. Keep signing keys, passwords, and private credentials out of the repository.

## 🐛 Feedback & Bug Reports

When reporting an issue, include:

- Device model and Android version.
- App version and distribution source.
- Steps to reproduce the problem.
- Expected and actual behavior.
- Relevant logs or screenshots, with sensitive information removed.

Never include Telegram bot tokens or signing credentials in public reports.

## 💬 Follow the Project

- 📲 [Google Play](https://play.google.com/store/apps/details?id=com.superpinger)
- ✈️ [Telegram — Unagi Lab](https://t.me/unagilab)
- 🐙 [GitHub — CyberUnagiMaki](https://github.com/CyberUnagiMaki)
- 📸 [Instagram — cyber_unagi_maki](https://www.instagram.com/cyber_unagi_maki/)

---

⭐ **If SuperPinger helps you troubleshoot your network, consider starring the repository!**
