# 🌀 TCL Air Conditioner Integration for Home Assistant

> 🇩🇪 Das ist ein Fork von sorz2122 und ich habe es an meine Bedürfnisse angepasst **  
> Einfaches DIY-Projekt mit ESP32 + USB-Kabel. Keine Cloud nötig.

---

## 🛠️ Was du brauchst

- **ESP32** (z. B. ESP32-C3, WROOM32, NodeMCU)
- **USB-A-Stecker oder -Kabel**  
- **Home Assistant mit ESPHome (ab Version 2023.3.0)**

---

## 🔌 Verkabelung

| USB-A Pin | Kabelfarbe | → ESP32 Pin |
|-----------|------------|--------------|
| GND       | Schwarz    | VIN/VCC      |
| D+        | Grün       | GND          |
| D-        | Grau       | RXD          |
| VBUS      | Rot        | TXD          |


## 🧠 Einrichtung in Home Assistant

> Die Lösung basiert auf **ESPHome** und funktioniert nur mit Home Assistant.

### 1. ESPHome installieren

- In Home Assistant unter **Einstellungen → Add-ons → ESPHome** installieren

### 2. Neues Gerät erstellen

- Im ESPHome-Dashboard → "New Device"
- Deinen ESP32-Typ auswählen, z. B. `esp32-c3-devkitm-1` oder `nodemcu-32s`

### 3. Konfiguration einfügen

#### Option A: Einfache Konfiguration
[📄 Sample_conf.yaml](https://github.com/httpneo/tclac/blob/master/Sample_conf.yaml)

#### Option B: Erweiterte Konfiguration
[📄 TCL-Conditioner.yaml](https://github.com/httpneo/tclac/blob/master/TCL-Conditioner.yaml)

📝 **Wichtig:**  
- WLAN-Daten, Gerätename etc. anpassen  
- Kommentare im YAML helfen beim Einrichten

### 4. Auf ESP32 flashen

- USB-Kabel anschließen oder OTA (Over-the-Air) verwenden

---

## 🔧 Erweiterte Konfiguration per Remote Package

Du kannst die Konfiguration modular laden:

```yaml
packages:
  remote_package:
    url: https://github.com/httpneo/tclac.git
    ref: master
    files:
      - packages/core.yaml   # Hauptmodul
      # - packages/leds.yaml # Optional
    refresh: 30s
