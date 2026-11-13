# Before-and-After Home Network Security Checklist

> **Project:** InternCircle Cybersecurity Internship – Project 04  
> **Document:** Network Hardening Verification Checklist  
> **Classification:** CONFIDENTIAL / AUDIT WORKPAPER  
> **Assessment Cycle:** Pre-Audit Baseline vs. Post-Remediation Hardening  
> **Assessor:** [Intern / Candidate Name]  
> **Verification Status:** Baseline Documented | Remediation Guidance Prepared  

---

## 1. Overview & Verification Methodology

This checklist tracks the transition of the home network from an unhardened, factory-default, or vulnerable baseline configuration (**"Before"**) to a hardened, defense-in-depth posture (**"After"**).

Each item maps directly to a specific architectural control on the gateway router or connected endpoints. The **"Evidence"** column links to verifiable audit artifacts (screenshots or configuration logs), and the **"Status"** column indicates whether the control has been fully verified or remains a pending placeholder for manual assessor confirmation.

> [!WARNING]
> **Safety and Reversibility Rule:** Never modify any router or device setting without first documenting the original value and creating an exported configuration backup. Network changes must be made one at a time over a wired connection where possible, verifying connectivity after each modification.

---

## 2. Before-and-After Security Audit Table

| Security Item | Before (Baseline State) | After (Hardened Target State) | Evidence | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Wi-Fi Password** | `[SAMPLE: Factory sticker PSK (8-10 alphanumeric characters), low entropy, susceptible to dictionary/handshake crack]` | `[SAMPLE: 20+ character Diceware passphrase with mixed-case, numbers, and symbols; stored in secure password manager]` | `[EVIDENCE: evidence/evidence_02_wifi_encryption_wpa.png - Masked passphrase field]` | `[PLACEHOLDER: Awaiting User Verification]` |
| **Wi-Fi Encryption** | `[SAMPLE: WPA2-Personal (TKIP/AES mixed mode) or open legacy cipher enabled]` | `[SAMPLE: WPA3-Personal (SAE) enabled, or WPA2/WPA3 Transitional Mode with PMF (Protected Management Frames) enforced]` | `[EVIDENCE: evidence/evidence_02_wifi_encryption_wpa.png - Security mode dropdown]` | `[PLACEHOLDER: Awaiting User Verification]` |
| **Router Admin Password** | `[SAMPLE: Default factory credentials (e.g., admin/admin, admin/password, or ISP default admin)]` | `[SAMPLE: Custom high-entropy password (18+ characters, non-dictionary, distinct from Wi-Fi PSK)]` | `[EVIDENCE: evidence/evidence_03_router_admin_credentials.png - Password change confirmation dialog]` | `[PLACEHOLDER: Awaiting User Verification]` |
| **Remote Administration** | `[SAMPLE: Remote WAN Web Management enabled on port 80/8080 or cloud remote access toggle active]` | `[SAMPLE: Remote Management (WAN) explicitly DISABLED; management restricted to local LAN/Wired Ethernet only]` | `[EVIDENCE: evidence/evidence_04_remote_management_disabled.png - Remote Management disabled toggle]` | `[PLACEHOLDER: Awaiting User Verification]` |
| **Router Firmware** | `[SAMPLE: Outdated firmware version v1.0.4 build 20220315; automatic notification unconfigured]` | `[SAMPLE: Firmware updated to latest vendor release v1.2.1 build 20240918; auto-check enabled]` | `[EVIDENCE: evidence/evidence_05_firmware_version_check.png - Firmware check screen showing "Latest Version Installed"]` | `[PLACEHOLDER: Awaiting User Verification]` |
| **Guest Network** | `[SAMPLE: Guest Wi-Fi disabled; all visitors and IoT peripherals connected to primary trusted LAN]` | `[SAMPLE: Dedicated Guest SSID configured on 2.4 GHz; AP/Client Isolation enabled; Intranet access blocked]` | `[EVIDENCE: evidence/evidence_06_guest_network_config.png - Guest network active with "Allow Guests to Access LAN: Disabled"]` | `[PLACEHOLDER: Awaiting User Verification]` |
| **Connected Devices** | `[SAMPLE: 10 connected assets including 1 unverified unknown device; no DHCP reservations or friendly names]` | `[SAMPLE: 100% of connected devices inventoried, labeled with static DHCP reservations; unknown device isolated/blocked]` | `[EVIDENCE: evidence/evidence_08_dhcp_device_table.png - DHCP client list with labeled hostnames]` | `[PLACEHOLDER: Awaiting User Verification]` |
| **Device Updates** | `[SAMPLE: OS automatic updates deferred on 2 endpoints; third-party software updates unmanaged]` | `[SAMPLE: Automatic OS security patches enabled on all Windows/macOS/iOS/Android devices; auto-update active]` | `[EVIDENCE: evidence/evidence_09_os_update_status.png - OS Windows Update / macOS Software Update showing "Up to Date"]` | `[PLACEHOLDER: Awaiting User Verification]` |
| **Data Backups** | `[SAMPLE: No systematic backup; vital files stored exclusively on local laptop hard drive without versioning]` | `[SAMPLE: 3-2-1 backup strategy implemented (Local encrypted external drive + Cloud automated backup with immutability)]` | `[EVIDENCE: evidence/evidence_10_backup_configuration.png - Backup software dashboard showing successful backup]` | `[PLACEHOLDER: Awaiting User Verification]` |

---

## 3. Extended Defense-in-Depth Hardening Controls

To provide comprehensive, enterprise-grade protection, the following technical controls are assessed alongside the primary checklist:

| Security Item | Before (Baseline State) | After (Hardened Target State) | Evidence | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Wi-Fi Protected Setup (WPS)** | `[SAMPLE: WPS enabled via Push Button (PBC) and 8-digit PIN]` | `[SAMPLE: WPS completely DISABLED (mitigating Reaver, Pixie Dust brute-force PIN attacks)]` | `[EVIDENCE: evidence/evidence_02_wifi_encryption_wpa.png - WPS toggle set to Disabled]` | `[PLACEHOLDER: Awaiting User Verification]` |
| **Universal Plug and Play (UPnP)** | `[SAMPLE: UPnP enabled by default, allowing local apps to dynamically open WAN ports]` | `[SAMPLE: UPnP DISABLED; port mappings audited and restricted to explicit manual rules if needed]` | `[EVIDENCE: evidence/evidence_07_upnp_disabled.png - UPnP service disabled toggle]` | `[PLACEHOLDER: Awaiting User Verification]` |
| **Management Protocol** | `[SAMPLE: Admin console accessible via unencrypted HTTP over local Wi-Fi]` | `[SAMPLE: Admin console forced to HTTPS; HTTP redirection active; admin session timeout set to 5-10 minutes]` | `[EVIDENCE: evidence/evidence_03_router_admin_credentials.png - Browser lock icon on router URL]` | `[PLACEHOLDER: Awaiting User Verification]` |
| **Default SSID Broadcast** | `[SAMPLE: Default vendor SSID broadcasted (e.g., 'TP-Link_5G_A490', revealing router make/model)]` | `[SAMPLE: Changed to neutral, non-identifying SSID (e.g., 'AuroraNet_5G', revealing no personal or hardware data)]` | `[EVIDENCE: evidence/evidence_02_wifi_encryption_wpa.png - SSID configuration field]` | `[PLACEHOLDER: Awaiting User Verification]` |
| **DNS Server Configuration** | `[SAMPLE: Default unencrypted ISP DNS servers with potential logging and ad redirection]` | `[SAMPLE: Configured secure, privacy-respecting DNS with DoH/DoT support (e.g., Cloudflare 1.1.1.2/1.0.0.2 with malware filtering or Quad9 9.9.9.9)]` | `[EVIDENCE: evidence/evidence_05_firmware_version_check.png - WAN DNS server settings]` | `[PLACEHOLDER: Awaiting User Verification]` |
| **WAN ICMP Echo (Ping Response)** | `[SAMPLE: Router responds to external WAN ping requests, exposing active IP to scanners]` | `[SAMPLE: 'Ignore Ping from WAN' / 'Stealth Mode' enabled; unassigned inbound ports silently dropped]` | `[EVIDENCE: evidence/evidence_04_remote_management_disabled.png - WAN Ping response unchecked]` | `[PLACEHOLDER: Awaiting User Verification]` |

---

## 4. Step-by-Step Assessor Verification & Action Guide

Follow this protocol to transition placeholders into verified audit data:

### Phase 1: Pre-Audit Snapshot (Documenting "Before" State)
1. **Router Backup:** Navigate to `System Tools > Backup & Restore` and download a `.bin` or `.conf` configuration snapshot.
2. **Access Security Screens:** Open router management interface in a web browser.
3. **Capture Baseline Screenshots:** Capture screen clippings of the following areas:
   - Wireless Security (SSID, Encryption, Password).
   - Administration / Management (Admin username, password change form, remote management).
   - System Information (Firmware version, release date).
   - Network Map / DHCP Client Table.
   - Advanced Features (WPS, UPnP, Guest Network).
4. **Endpoint Inspection:** Check Windows Update / macOS System Settings, verify BitLocker/FileVault status, and check backup status.

### Phase 2: Applying Safe Hardening Changes (Executing "After" State)
1. **Change Passwords First:** Update router admin password to a 20-character secret. Next, update Wi-Fi PSK.
2. **Disable Risky Protocols:** Toggle WPS to **Disabled**. Toggle UPnP to **Disabled**. Toggle Remote Management to **Disabled**.
3. **Configure Guest Network:** Enable Guest Wi-Fi, assign a unique passphrase, and enable **Client Isolation** (or "Isolate from LAN").
4. **Update Firmware:** Check the vendor support website for the newest signed firmware binary for your exact hardware revision. Follow on-screen vendor flashing procedures using a wired Ethernet connection.

### Phase 3: Post-Remediation Verification & Evidence Archival
1. Re-open each settings page to verify settings persisted through reboot.
2. Save screenshots into the `evidence/` directory following the naming format specified in `evidence/README.md`.
3. In the checklist table above, replace `[SAMPLE: ...]` and `[PLACEHOLDER: Awaiting User Verification]` with `[VERIFIED]` and your actual observed values.
