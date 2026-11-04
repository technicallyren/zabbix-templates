# zabbix-templates

Tested templates for **Zabbix 7.0+ LTS**.

---

## 📂 Repository Structure

```text
templates/
├── network/          # Routers, switches, APs (planned)
├── servers/          # Linux / Windows systems (planned)
└── printers/
    └── zebra/        # Zebra Link-OS industrial printers
```
---

## 📋 Available Templates

| Category | Device / Model | Directory | Description |
| :--- | :--- | :--- | :--- |
| **Printers** | Zebra Link-OS (ZD420) | [`templates/printers/zebra/`](templates/printers/zebra/) | SNMP telemetry: odometers, printhead life, cutter counter, sensor states, Wi-Fi RSSI |

---

## 🚀 Quick Start

1. Download the `.yaml` template from the target `templates/` subdirectory.
2. In the Zabbix UI, go to **Data collection** $\rightarrow$ **Templates** $\rightarrow$ **Import**.
3. Select the file and confirm the import.
4. Link the template to your host and configure the SNMP interface (Port `161`, SNMP community / v3 credentials).
5. Adjust user macros (`{$ZEBRA...}`, `{$ICMP...}`) under host settings if custom thresholds are needed.

---

## 📄 License

Licensed under the **MIT License**. Free to use and modify with author attribution required.

**Authors:** Rene Holasek & Pavel Cervenicky (*Autodoc Czech IT Team*)
