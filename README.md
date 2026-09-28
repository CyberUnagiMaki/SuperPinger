📡 SuperPinger — Network Tools & Monitoring
Understand your connection. Monitor your hosts. Keep your network under control.
SuperPinger is an Android toolkit for network diagnostics, live traffic monitoring, and host availability checks. Troubleshoot your home Wi-Fi, check a remote server, or investigate an unstable connection from your phone.
📲 Download SuperPinger on Google Play
This README describes the 1.8 feature set. Availability in the store depends on the published release.

✨ What’s New
- 🤖 Telegram bot alerts for favorite hosts going offline or recovering.
- 📊 Live download and upload graphs for Wi-Fi and mobile data.
- 📱 Traffic widgets, including a compact mode without a graph.
- 🔎 Extended diagnostics for TCP ports, DNS, IPv4, IPv6, and HTTPS.
- 📈 Network quality history grouped by profile, network type, host, and test method.
- ⚖️ Before-and-after comparisons of saved diagnostic sessions.
- 📤 Support reports with a summary and latency graph.
- ⭐ Customizable shortcuts on the home screen.
- ⏱️ Automatic stop timers for monitoring sessions.
- 🔕 Quiet mode for eight hours.
🧰 Network Tools
Tool	What it does
🎯 Ping	Check response times, packet loss, and availability with live graphs and configurable test settings.
🛤️ Traceroute	Investigate the route to a destination and review available hop information.
📶 Network Scanner	Discover responding devices on your local network.
🌐 DNS Lookup	Query DNS records and inspect domain resolution.
🚪 Port Scanner	Check which TCP ports respond on a host.
📋 WHOIS Lookup	View available registration information for domains and IP addresses.
⭐ Favorites	Save frequently checked hosts for quick access and monitoring.
🕘 History	Review previous checks and export results.


📊 Live Traffic Monitoring
See how much data your device is receiving and sending while connected to Wi-Fi or a mobile network.
- Live download and upload speeds.
- A graph of recent traffic activity on the home screen.
- Daily and monthly data usage.
- Separate Wi-Fi and mobile usage totals.
- A configurable mobile data limit with an alert.
Historical traffic totals require access to Android usage statistics. Mobile usage availability depends on the Android version and device.
📱 Home Screen Widgets
Keep connection information visible without opening the app.
- Download and upload speeds.
- A recent traffic graph.
- Compact mode without the graph.
- Light, dark, and system appearance options.
- Configurable colors and update intervals.
- A preview in More.
- A Quick Settings tile for convenient monitoring control.
Traffic monitoring is enabled from More, with a battery-use warning before activation. Widget settings apply to all traffic widget instances.
🤖 Telegram Bot Alerts
Connect your own Telegram bot and receive host availability updates in your group.
Setup
1. Create a bot using @BotFather in Telegram.
2. Add the bot to your group and allow it to send messages.
3. Open More → Telegram Bot.
4. Enter the bot token and numeric group chat ID.
5. Enable event delivery and save the settings.
6. Send a test message.
7. Add hosts to Favorites and enable host monitoring.
How alerts work
- Two matching checks confirm an unavailable or recovered state.
- The initial successful check does not generate an alert.
- Losing internet access on the phone does not mark every host as offline.
- Pending events can be retried after temporary delivery failures.
- Quiet mode sends Telegram messages without notification sound.
The bot token is encrypted using Android Keystore and is excluded from application reports.
Alerts depend on the configured check interval and Android background restrictions. Delivery can be delayed, and network failures can occasionally cause duplicate messages. Host names and addresses are shared with the configured Telegram group.

🔎 Extended Diagnostics
🚦 Quick Connection Check
Check the local gateway, an external TCP endpoint, DNS, and HTTPS. Review response times and possible explanations for connection problems.
🚪 Custom TCP Port
Test a port of your choice or configure a TCP port in a diagnostic profile.
🌍 IPv4 and IPv6
Inspect connection results separately for the addresses returned by DNS. See when an address family is unavailable.
🧭 DNS Comparison
Compare system DNS results with Google and Cloudflare DNS over HTTPS, including A/AAAA records and request timings.
🔐 HTTPS and TLS
Inspect:
- HTTP response status.
- Request duration.
- TLS certificate expiry.
- Estimated days until certificate expiration.
HTTPS checks use certificate validation and do not bypass TLS errors.
DNS over HTTPS timings include HTTPS overhead, while system DNS may return cached results. These measurements are not a direct ranking of DNS server speed.

📈 Stability Monitoring
Create profiles for Home, Work, Gaming, or your own servers.
- Monitor up to five hosts in a diagnostic session.
- Choose ICMP, TCP, or automatic fallback.
- Review minimum, average, and maximum latency.
- Track packet loss and jitter.
- Measure observed periods without successful replies.
- Configure alert thresholds and cooldowns.
- Review network changes and session events.
Quality history groups results by profile name, network type, host, and measurement method. Separate profile names help distinguish locations such as home and work.
📁 Reports & Comparisons
Turn diagnostic results into information you can review or share.
- Export session summaries and measurement data.
- Save CSV data for further analysis.
- Compare two saved sessions before and after a network change.
- Review differences in latency, loss, jitter, and observed outages.
- Generate a compact support ZIP containing a text summary and PNG latency graph.
Reports are shared through Android’s share menu when you choose to export them.
⚙️ Personalization & Monitoring Controls
- 🌙 Light, dark, and system themes.
- ⭐ Favorite diagnostic tools on the home screen.
- ⏱️ Stop timers from 1 to 1,440 minutes, or manual stopping.
- 🔕 Eight-hour quiet mode with an option to resume alerts.
- 🔔 Persistent monitoring notifications with stop controls.
- 🔋 Battery-use warnings before enabling background monitoring.
Timer settings apply to the next monitoring, diagnostic, or traffic-widget session.
🔒 Data & Permissions
History, profiles, and reports are stored on the device. Network checks contact the selected hosts and services. Enabling Telegram alerts sends the configured monitoring events to Telegram.
Some features require additional Android access:
Permission or access	Purpose
Notifications	Monitoring alerts, traffic-limit warnings, and service controls.
Usage access	Daily and monthly device traffic statistics.
Location permission	Access to the connected Wi-Fi network name where Android requires it.
Phone state	Mobile network type and available signal information.


The application does not use GPS to track your movements.
Advertising SDKs may process data according to their privacy policies. The Google Play edition uses Google AdMob; the separate RuStore edition uses Yandex Mobile Ads.
ℹ️ Understanding the Results
- A missed ping does not necessarily mean a server is offline: some hosts block ICMP.
- A closed TCP port does not prove that the internet connection is broken.
- Automatic fallback can combine results from different test methods.
- Android battery optimization and device sleep can delay background checks.
- Background monitoring can increase battery consumption.
- SuperPinger helps diagnose connection problems; it does not increase internet speed.
For meaningful comparisons, use the same hosts, methods, ports, and similar test durations.
🛠️ Build from Source
The prepared 1.8 source projects use:
- Kotlin
- Minimum Android version: Android 7.0 / API 24
- Compile and target SDK: 36
- Android Gradle Plugin: 9.0.1
- Gradle: 9.1.0
- Gradle JDK: 21
Open the project in a compatible Android Studio version, configure the Android SDK, and sync Gradle.
To verify the source without packaging an APK:
./gradlew :app:compileDebugKotlin :app:compileReleaseKotlin :app:testDebugUnitTest :app:lintDebug
On Windows:
.\verify_sources.bat
To include release optimization with R8:
.\verify_optimized_sources.bat
Use your own signing configuration when preparing a release. Keep signing keys, passwords, and private credentials out of the repository.
🐛 Feedback & Bug Reports
When reporting an issue, include:
- Device model and Android version.
- App version and distribution source.
- Steps to reproduce the problem.
- Expected and actual behavior.
- Relevant logs or screenshots, with sensitive information removed.
Never include Telegram bot tokens or signing credentials in public reports.
💬 Follow the Project
- 📲 Google Play
- ✈️ Telegram — Unagi Lab
- 🐙 GitHub — CyberUnagiMaki
- 📸 Instagram — cyber_unagi_maki
⭐ If SuperPinger helps you troubleshoot your network, consider starring the repository!
