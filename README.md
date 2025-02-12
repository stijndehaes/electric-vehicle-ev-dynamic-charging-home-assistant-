# Dynamic EV Charging Automation for Home Assistant

This project automates the charging current of an electric vehicle based on household power consumption.  
It works with **any EV (Tesla, Mercedes, Ford, BYD, etc.)** or **any EV charger** as long as it is integrated and can be controlled within Home Assistant.

This blueprint dynamically adjusts the charging rate, ensuring that the vehicle uses the **maximum available power** without exceeding the contracted limit.  
It also supports **different power limits for day and night** to optimize charging based on electricity tariffs.

**If you found this project helpful, please consider buying me a coffee!**

<div align="center">
  <a href='https://ko-fi.com/K3K819CO23' target='_blank'>
    <img height='36' style='border:0px;height:36px;' 
         src='https://storage.ko-fi.com/cdn/kofi6.png?v=6' border='0' 
         alt='Buy Me a Coffee at ko-fi' />
  </a>
</div>

---

## 📥 Installation

This blueprint can be installed in two ways:

### **🔗 Direct Import via Home Assistant**
https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FEDV11%2Felectric-vehicle-ev-dynamic-charging-home-assistant-%2Fblob%2F55aff6f887136b29e311d646cfaea37b93042f07%2FDynamic-EV-Charging-Automation.yaml

### **📂 Manual Installation**
1. Open the blueprint file in this repository (https://github.com/EDV11/electric-vehicle-ev-dynamic-charging-home-assistant-/blob/55aff6f887136b29e311d646cfaea37b93042f07/Dynamic-EV-Charging-Automation.yaml).
2. Copy the URL from your browser's address bar.
3. In Home Assistant, go to **Settings → Automations & Scenes → Blueprints**.
4. Click **"Import Blueprint"** in the bottom right corner.
5. Paste the URL and click **"Preview Blueprint"**.
6. Click **"Import Blueprint"** to finalize.

---

## 🔌 🚗 🔋 Tested Hardware  

This is some of the hardware I've used and tested with this automation:  

- [Shelly EM Energy Meter](https://amzlink.to/az0UFbhU9htEu)  
- Tesla car with [Tesla Fleet integration](https://www.home-assistant.io/integrations/tesla_fleet/).  
  - [Buy your Tesla with a discount through this link](https://ts.la/eduardo432919)  
- [Feyree Type 2 portable 7kW charger](https://s.click.aliexpress.com/e/_opguDAp)  
- [Feyree Type 2 Wallbox](https://s.click.aliexpress.com/e/_oEFZ75f)  

Just to be clear, if you can control your car from Home Assistant and have access to its sensors, you can use this automation without a connected charger.

---

## 🔧 Requirements

Before using this blueprint, you need the following:

- **Total Power Consumption Sensor** (e.g., <a href="https://amzlink.to/az0UFbhU9htEu" target=_blank>Shelly EM Gen3</a> is recommended if you don’t have one. You can get it from that link).
- **Your EV or Charger integrated into Home Assistant**, exposing the necessary sensors. I use this <a href="https://s.click.aliexpress.com/e/_opguDAp" target=_blank>Feyree portable charger</a>, I haven't tested with any other.
- **Basic information about your electricity contract**, including:
  - Grid voltage (e.g., 230V for EU, 120V for the US).
  - Maximum grid power limits (contracted power).
  - Day and night tariff periods (if applicable).

---

## ⚙️ Configuration

The following parameters need to be configured:

- **Charging interval** (1, 3, or 5 minutes).
- **A device tracker** (preferably the car) to ensure that the automation runs only when the EV is at home.
- **A charging status sensor** to ensure changes are only made when the EV is actively charging.
- **Total power consumption sensor** (measured in watts).
- **Maximum Grid Power (Day)** – Set to **0** if you only want to charge at night.
- **Maximum Grid Power (Night)**.
- **Charging current control entity** – The EV or charger must support dynamic amperage control.
- **Grid voltage**.
- **Maximum charging amperage** – The system will never exceed this limit, even if extra power is available.
- **Minimum charging amperage** – The system will stop charging if power availability drops below this threshold.
- **Day-time period settings** (Define when "day" mode applies, typically when electricity is more expensive or power is limited).

---

## 🚀 How It Works

The automation runs every **1, 3, or 5 minutes**, depending on the selected interval.  
It **only** adjusts the charging rate if the EV is **charging** and **at home**.  

### **Dynamic Load Adjustment**
The automation continuously monitors household power usage and dynamically **adjusts the charging current** to avoid exceeding the contracted power limit.  
If a high-power appliance (e.g., oven, stove, heating) is turned on, the charging rate will **automatically decrease** to prevent overloading.  
Once power consumption drops, the EV will **resume charging at the maximum allowed rate**.

### **Day & Night Power Limits**
Many electricity contracts offer **cheaper power at night**, along with **higher power limits**.  
This blueprint allows setting **different power limits for day and night**, ensuring that charging is optimized based on your tariff structure.

---

## ❓ Reporting Issues & Community Discussion

If you encounter issues or have suggestions for improvements, please check the **Home Assistant Forum thread** for support.  
_(A link to the forum thread will be added here.)_

---

## 📜 License

This project is released under the **MIT License**, which means you are free to **download, modify, and share it** as you like.

If you prefer **Creative Commons**, the most suitable option would be **CC BY-SA 4.0** (Attribution-ShareAlike), which allows modifications as long as credit is given.

Would you like to use **MIT**, **CC BY-SA 4.0**, or another license? Let me know, and I’ll finalize this section accordingly!
