# Zabbix Template: Canon Printer

A SNMP template for Canon printers (developed and tested on **Canon iR-ADV C5840**). 
Fully compatible with Zabbix 7.0.

This template features automatic discovery for supplies, trays, and network interfaces, while strictly adhering to the RFC 3805 printer standards.
## ✨ Key Features

* **Consumables (LLD):** Monitors Toners and Waste Toner containers. Gracefully handles unmeasurable levels (start-up/non-original toners) via Value Mapping.
* **Paper Trays (LLD):** Tracks paper levels, dimensions, and types across all standard and multi-purpose trays.
* **Network Health (LLD):** Tracks interface status, traffic, and includes a specific protection trigger against PDF print spooling memory exhaustion.
* **Hardware Sensors (LLD):** Monitors door and interlock states (Open/Closed).
* **General Health:** ICMP Ping, Packet Loss, and Uptime (with restart detection).

## ⚙️ Macros (Configuration)

You can adjust the following macros directly on your host to change the alerting thresholds:

| Macro | Default | Description |
| :--- | :--- | :--- |
| `{$CANON.NET.DATA.WARN}` | `1545188227` | Bytes limit (~1.5GB) for network inbound traffic. High PDF spooling can freeze the printer memory. Alerts to recommend a restart. |
| `{$PAPERINFO}` | `10` | Low paper warning threshold (number of papers). |
| `{$TONERINFO}` | `3` | Low toner warning threshold (%). |
| `{$TONEREMPTY}` | `0` | Critical empty toner threshold (%). |
| `{$WASTEINFO}` | `5` | Waste toner almost full warning threshold (%). |
| `{$WASTEFULL}` | `0` | Critical waste toner full threshold (%). |

*(Note: Toner and Waste triggers safely ignore `-1`, `-2`, and `-3` SNMP states to prevent false alarms.)*

## 🚀 Setup Instructions

1. Import the `.yaml` file into your Zabbix server (`Data collection` -> `Templates` -> `Import`).
2. Assign the template to your Canon printer host.
3. Configure the **SNMP interface** on the host (Port 161, correct SNMPv2 community or SNMPv3 credentials).
4. *(Optional)* Adjust the host macros if your operational limits differ from the defaults.
