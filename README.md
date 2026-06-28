# Centralina Pioggia RG-09

[![ESPHome](https://img.shields.io/badge/ESPHome-2025.8.2-green)](https://esphome.io/)
[![ESP32](https://img.shields.io/badge/ESP32-Dev-blue)](https://esphome.io/components/esp32.html)

Questa configurazione ESPHome implementa una centralina per il monitoraggio delle precipitazioni utilizzando il sensore di pioggia ottico Hydreon RG-09 e un sensore di temperatura DS18B20.

## Hardware

- [ESP32 Development Board](https://esphome.io/components/esp32.html)
- [Hydreon RG-09](https://hydreon.com/wp-content/uploads/sites/3/2018/01/RG-9_Instructions.pdf) - Sensore ottico di pioggia
- [DS18B20](https://www.maximintegrated.com/en/products/sensors/DS18B20.html) - Sensore di temperatura waterproof (one-wire)

## Funzionalità

- **Monitoraggio precipitazioni**: Rileva e quantifica la pioggia tramite sensore ottico RG-09
- **Monitoraggio temperatura**: Temperatura esterna via DS18B20 e temperatura interna del sensore RG-09
- **Diagnostica sensore**: Monitoraggio stato lente (sporca/pulita), condizioni termiche e saturazione emettitore
- **Wi-Fi con fallback**: Configurazione rete principale con hotspot di fallback
- **Captive Portal**: Interfaccia web per la configurazione Wi-Fi in caso di mancata connessione
- **API Home Assistant**: Integrazione automatica con Home Assistant
- **OTA Updates**: Aggiornamenti Over-The-Air tramite ESPHome

## Collegamenti fisici

- **UART per RG-09**:
  - RX: GPIO16
  - TX: GPIO17
  - Baudrate: 9600
- **OneWire per DS18B20**:
  - Pin dati: GPIO32

## Entità esposte

| Nome | Tipo | Descrizione |
|------|------|------------|
| Livello Pioggia | Sensore | Quantità di precipitazioni rilevata |
| Temperatura esterna | Sensore | Temperatura esterna rilevata dal DS18B20 |
| RG-09: temperatura sensore | Sensore | Temperatura interna del sensore RG-09 |
| RG-09: Troppo Freddo | Binario | Stato temperatura operativa del sensore |
| RG-09: Lente Sporco | Binario | Stato pulizia della lente del sensore |
| RG-09: Emettitore Saturo | Binario | Stato saturazione dell'emettitore ottico |

## Installazione

1. Includere questa configurazione nel proprio progetto ESPHome
2. Configurare le password necessarie (password hotspot Wi-Fi e OTA)
3. Compilare e caricare sul dispositivo

## Rilevamento indirizzo sensore DS18B20

_(Facoltativo: se non si usano altri sensori 1-Wire non dovrebbe essere ecessario specificare l'indirizzo)_
Per identificare l'indirizzo del sensore DS18B20, caricare inizialmente la configurazione senza specificare l'indirizzo. Dopo il primo avvio, controllare i log di ESPHome dove verrà mostrato l'indirizzo del sensore rilevato. Quindi decommentare la riga `address` nel file di configurazione e inserire l'indirizzo trovato.
