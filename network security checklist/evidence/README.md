# Evidence Repository & Screenshot Capture Guidelines

> **Project:** InternCircle Cybersecurity Internship – Project 04  
> **Folder:** `/evidence`  
> **Purpose:** Repository for Audited Configuration Screenshots & Verification Artifacts  
> **Classification:** CONFIDENTIAL / AUDIT EVIDENCE  

---

## 1. Overview & Objective

In a professional cybersecurity audit, findings are only as credible as the supporting evidence. Screenshots and configuration logs serve as the verifiable proof that controls were inspected, vulnerabilities were identified, and remediation actions were implemented.

This directory stores all visual evidence referenced throughout the audit report and before-and-after checklist.

---

## 2. Screenshot Naming Standards

To maintain audit consistency and ensure seamless automated report compilation, name all captured screenshot files using the standardized naming schema below:

| Standard Filename | Audit Control Area | Required Screen Content |
| :--- | :--- | :--- |
| `evidence_01_router_login_status.png` | Admin Authentication | Router web interface login screen; showing HTTPS status in URL bar |
| `evidence_02_wifi_encryption_wpa.png` | Wi-Fi Security Settings | Wireless configuration page showing SSID, WPA2/WPA3 mode, and WPS toggle |
| `evidence_03_router_admin_credentials.png` | Admin Credential Security | Password change form verifying non-default password configuration |
| `evidence_04_remote_management_disabled.png` | Remote Access Controls | Advanced/Remote Management page showing "Disabled" state and WAN ping response |
| `evidence_05_firmware_version_check.png` | Firmware Lifecycle | System status / Firmware update page showing current version and online check |
| `evidence_06_guest_network_config.png` | Network Segmentation | Guest Network settings showing enabled state, dedicated SSID, and AP Isolation |
| `evidence_07_upnp_disabled.png` | Inbound Port Security | Advanced NAT / UPnP page showing UPnP service toggle set to Disabled |
| `evidence_08_dhcp_device_table.png` | Asset Discovery | DHCP client lease list or Network Map showing all connected devices |
| `evidence_09_os_update_status.png` | Endpoint Patching | Windows Update / macOS Software Update showing system is fully up to date |
| `evidence_10_backup_configuration.png` | Disaster Recovery | Backup software dashboard showing recent successful automated backup |

---

## 3. Strict Data Redaction & Sanitization Protocol

> [!CAUTION]
> **Mandatory Sanitization Rule:** Prior to committing any screenshots to this repository or publishing your final audit report, you **MUST** obscure, blur, or black out all personally identifiable information (PII) and sensitive security credentials.

### What Must Be Redacted:
1. **Public IP Address (WAN IP):** Redact or obscure any public IPv4 or IPv6 address assigned by your Internet Service Provider. (Private IPs such as `192.168.1.xxx` or `10.0.0.xxx` are standard RFC 1918 subnets and do not need full redaction, but client host octets may be masked).
2. **Wi-Fi Pre-Shared Key (Passphrase):** Never expose cleartext or masked Wi-Fi passwords.
3. **Router Admin Credentials:** Never show cleartext passwords.
4. **Physical MAC Addresses:** Mask the last 6 characters (last 3 octets) of any MAC address (e.g., `BC:D0:74:XX:XX:XX`). Retaining the first 3 octets is acceptable as it only reveals the hardware vendor OUI.
5. **Personal Identifiers:** Black out ISP account numbers, customer names, street names, phone numbers, or email addresses that appear in router header banners or account portals.

### Recommended Free Redaction Tools:
- **Windows:** Snipping Tool / Paint (Use the black solid rectangle tool or blur tool).
- **macOS:** Preview (Tools > Annotate > Rectangle filled with solid color).
- **Cross-Platform:** GIMP, Greenshot, or Flameshot.

---

## 4. Visual Evidence Mockups & Verification Expectations

Below are visual architectural wireframes representing what each screenshot should capture:

### Mockup 1: Wireless Security Configuration (`evidence_02_wifi_encryption_wpa.png`)
```text
+--------------------------------------------------------------------------+
| ROUTER MANAGEMENT CONSOLE - WIRELESS SETTINGS                            |
+--------------------------------------------------------------------------+
|  Wireless Radio:          [X] Enable 2.4 GHz   [X] Enable 5 GHz          |
|  Network Name (SSID):     [ AuroraNet_5G ]                               |
|  SSID Broadcast:          [X] Enabled                                    |
|                                                                          |
|  Security Mode:           [ WPA2-Personal (AES) / WPA3-Personal (SAE) ]  |
|  Encryption:              [ AES-CCMP ]                                   |
|  Pre-Shared Key:          [ ************************************ ]       |
|                                                                          |
|  Wi-Fi Protected Setup:                                                  |
|  WPS Status:              ( ) Enabled   (*) DISABLED <--- [HARDENED]     |
|                                                                          |
|  [ Save Changes ]   [ Cancel ]                                           |
+--------------------------------------------------------------------------+
```

### Mockup 2: Remote Administration Controls (`evidence_04_remote_management_disabled.png`)
```text
+--------------------------------------------------------------------------+
| ROUTER MANAGEMENT CONSOLE - SYSTEM / REMOTE ACCESS                       |
+--------------------------------------------------------------------------+
|  Remote Web Management:                                                  |
|  Remote Management:       ( ) Enabled   (*) DISABLED <--- [CRITICAL]     |
|  Management Port:         [ 8080 ]                                       |
|  Allowed Remote IP:       ( ) Any IP address                             |
|                           (*) Only this IP: [ 0.0.0.0 ]                  |
|                                                                          |
|  WAN Ping Response:                                                      |
|  Respond to ICMP Echo:    [ ] Enable WAN Ping Response (Unchecked)       |
|                                                                          |
|  Local Management Access:                                                |
|  HTTPS Access Only:       [X] Enabled                                    |
|  Session Inactive Timeout:[ 10 ] minutes                                 |
+--------------------------------------------------------------------------+
```

### Mockup 3: Guest Network Segmentation (`evidence_06_guest_network_config.png`)
```text
+--------------------------------------------------------------------------+
| ROUTER MANAGEMENT CONSOLE - GUEST NETWORK CONFIGURATION                  |
+--------------------------------------------------------------------------+
|  Guest Network Status:    (*) Enabled   ( ) Disabled                     |
|  Guest SSID:              [ Aurora_Guest_IoT ]                           |
|  Security Mode:           [ WPA2-Personal (AES) ]                        |
|  Guest Password:          [ ******************** ]                       |
|                                                                          |
|  Access Restrictions:                                                    |
|  Allow Guests to see each other (Client Isolation): [ ] Disabled / ON    |
|  Allow Guests to access Local Network (LAN):        [ ] DISABLED <---    |
|                                                                          |
|  [ Apply Settings ]                                                      |
+--------------------------------------------------------------------------+
```

### Mockup 4: Universal Plug and Play (`evidence_07_upnp_disabled.png`)
```text
+--------------------------------------------------------------------------+
| ROUTER MANAGEMENT CONSOLE - UPnP ADVANCED CONFIGURATION                  |
+--------------------------------------------------------------------------+
|  UPnP Feature Status:                                                    |
|  Current Status:          DISABLED <--- [HARDENED]                       |
|  Enable UPnP:             [ ] (Unchecked)                                |
|                                                                          |
|  Active Port Mappings List:                                              |
|  (No dynamic UPnP port forward mappings present)                         |
|                                                                          |
|  [ Save ]   [ Refresh ]                                                  |
+--------------------------------------------------------------------------+
```

---

## 5. How to Insert Your Real Screenshots

When you conduct your live router verification:
1. Capture your actual router management screens matching the 10 categories above.
2. Apply solid black redaction boxes over sensitive keys, MAC octets, and WAN IPs.
3. Save each image as a PNG into this directory (`/evidence`) using the exact filenames listed in Section 2.
4. Verify that the filenames match the markdown image links in `report/Home_Network_Security_Audit_Report.md`.
