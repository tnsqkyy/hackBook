# Aircrack‑NG

The **Aircrack‑NG suite** is the fundamental toolkit for wireless security testing. It provides everything needed to capture 802.11 traffic, collect WPA/WPA2 handshakes, perform deauthentication attacks, convert capture formats, and crack keys.

This guide is based on my first practical Wi‑Fi hacking workflow, rewritten clearly and structured for learning.

---

## 📌 Overview

Aircrack‑NG is used for:

* Placing a wireless interface into monitor mode
* Capturing 802.11 frames
* Scanning access points and clients
* Forcing clients to reauthenticate (deauth attacks)
* Capturing WPA/WPA2 4‑way handshakes
* Converting captures into crackable formats
* Attempting password recovery

This section focuses on understanding *how* each step works — not just which commands to type.

---

## 1. Identify Your Wireless Interface

Before doing anything, determine the **actual interface name**.

```bash
ip link
```

Typical names include:

* `wlan0`
* `wlp2s0`
* `wlx<mac>`

You must use this name correctly before enabling monitor mode.

---

## 2. Install Aircrack‑NG

Debian/Ubuntu:

```bash
sudo apt install aircrack-ng
```

Arch:

```bash
sudo pacman -S aircrack-ng
```

Kali: preinstalled.

---

## 3. Check Wireless Card Capabilities

Not all wireless cards support monitor mode or packet injection.

Test monitor mode support:

```bash
iw list | grep -A 10 "Supported interface modes"
```

Look for:

* `monitor`
* `AP`
* `managed`

---

## 4. Enable Monitor Mode

Use `airmon-ng`:

```bash
sudo airmon-ng start <interface>
```

This usually creates a new interface:

* `wlan0` → `wlan0mon`

Alternatively, using `iw` manually:

```bash
sudo ip link set <interface> down
sudo iw <interface> set monitor control
sudo ip link set <interface> up
```

Monitor mode allows the card to **capture raw 802.11 frames**.

---

## 5. Scan Nearby Wi‑Fi Networks

Use **airodump‑ng** to list APs and stations:

```bash
sudo airodump-ng <monitor-interface>
```

Key fields:

* **BSSID:** MAC address of AP
* **PWR:** signal strength
* **CH:** channel
* **ENC:** encryption (WPA2/WPA3)
* **STATION:** connected clients

---

## 6. Capture a WPA Handshake

Target a specific AP on its channel:

```bash
sudo airodump-ng -c <channel> --bssid <AP_MAC> -w capture <monitor-interface>
```

When a client connects or reconnects, the tool will capture the **4‑way handshake**.

If no clients reconnect naturally, trigger a deauth attack.

---

## 7. Force a Device to Reauthenticate (Optional)

Use `aireplay-ng` to send deauthentication frames:

```bash
sudo aireplay-ng --deauth 10 -a <AP_MAC> <monitor-interface>
```

This forces clients to drop and reconnect, creating the handshake.

---

## 8. Crack the Captured Handshake

Once you have `capture.cap`:

```bash
aircrack-ng -w wordlist.txt capture.cap
```

Cracking depends entirely on the strength of the password.

---

## 📚 Notes & Understanding

* Monitor mode lets your card listen to raw frames instead of only traffic destined for you.
* WPA2 is not “broken”; you rely on weak passwords.
* Deauth frames are unprotected in 802.11 → easy to spoof.
* Capturing is legal only on networks you own or have explicit permission to test.

---

## 🚀 Next Tutorials

More wireless tools will be added:

* **hcxdumptool** (PMKID attack)
* **hcxpcapngtool** (hash conversion)
* **wifite** (automation)

For now, start practicing with Aircrack‑NG — it builds the foundation for everything above.

