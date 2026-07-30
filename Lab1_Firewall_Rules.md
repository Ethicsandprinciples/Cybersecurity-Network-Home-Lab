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
-  Debian terminal showing successful baseline pings vs. timed-out pings post-rule.
- [Screenshot 2] pfSense LAN firewall rule configuration table.
- [Screenshot 3] System log event showing blocked ICMP packets with red drop indicators.
