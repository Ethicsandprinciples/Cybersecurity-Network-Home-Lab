# Lab 1: Gateway Firewall Rule Engineering & Traffic Isolation

## Objective
Configure custom firewall rules on a pfSense virtual gateway to inspect, drop, and log ICMP traffic originating from internal Linux endpoints.

## Infrastructure & Topology
* **Gateway:** pfSense 2.7.x (Virtual Machine)
* **Client Host:** Debian 12 (LAN Interface)
* **Target:** External IP (`1.1.1.1`)

## Execution & Steps
1. **Baseline Verification:** Executed `ping 1.1.1.1` on Debian host; verified successful 64-byte reply sequence.
2. **Rule Implementation:** Added top-priority drop rule on pfSense LAN interface:
   - Action: Block
   - Protocol: ICMP
   - Logging: Enabled
3. **Verification:** Re-executed ICMP request; confirmed 100% packet loss.
4. **Telemetry Inspection:** Audited pfSense firewall logs (`Status > System Logs > Firewall`) to confirm rule match hits.

## Key Screenshots Included
- <img width="1310" height="806" alt="Screenshot 2026-07-30 015834" src="https://github.com/user-attachments/assets/102a643d-a801-40d4-8c59-fdffa15486e2" />
 Debian terminal showing successful baseline pings vs. timed-out pings post-rule.
- <img width="1301" height="806" alt="Screenshot 2026-07-30 015741" src="https://github.com/user-attachments/assets/01bd5ff1-0b61-44c0-ad00-07563fd09ccd" /> pfSense LAN firewall rule configuration table.
- <img width="1293" height="798" alt="Screenshot 2026-07-30 020027" src="https://github.com/user-attachments/assets/b0d906ef-b7c9-4d16-9279-31d2aad2ec1e" />
 System log event showing blocked ICMP packets with red drop indicators.
