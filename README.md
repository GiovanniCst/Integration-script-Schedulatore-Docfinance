# Schedulatore to DocFinance Integration Script  
  
(IT) Script Python per connettere "DocFinance (tm)" con "Schedulatore (tm)". Monitora cartelle, sposta file, utilizza watchdog, e può essere un servizio Windows con NSSM.
  
(EN) Python script to connect "DocFinance (tm)" with "Schedulatore (tm)". Monitors folders, moves files based on prefixes/extensions, uses watchdog, and can be a Windows service via NSSM.  
    
**Italian:**
  
# Script di Integrazione tra DocFinance e Schedulatore

Questo repository contiene uno script Python originale progettato da Giovanni Costantini, Pesaro per connettere il software "DocFinance (tm)" di DocFinance S.r.l. (Reggio Emilia, Italia, https://www.docfinance.net/) con il software "Schedulatore (tm)" di Cariparma / Crédit Agricole Bank. Questa integrazione colma il divario tra questi due sistemi, che non sono integrati nativamente.

## Funzionalità

- **Monitoraggio delle Cartelle**: Utilizza il modulo watchdog per monitorare in tempo reale le cartelle specificate.
- **Spostamento Basato sui Prefissi**: Sposta i file in base ai prefissi predefiniti.
- **Spostamento Basato sulle Estensioni**: Sposta i file in base alle estensioni predefinite.
- **Regole di Spostamento Speciali**: Gestisce lo spostamento dei file SEPA Credit Trans ed SDD, nonché la Presentazione RIBA e il pagamento riba fornitori.
- **Logging**: Utilizza TimedRotatingFileHandler per creare un nuovo file di log ogni giorno, registrando dettagliatamente le attività di spostamento dei file e gli eventuali errori.
- **Configurazione come Servizio su Windows**: Configurato con successo come servizio su Windows Server tramite NSSM (Non-Sucking Service Manager).

## Specifiche

- **Versione Python**: Python 3.x
- **Moduli Richiesti**: os, shutil, logging, configparser, watchdog, time
- **File di Configurazione**: config.ini
- **File di Log**: file_mover.log

## Requisiti

- Python 3.x
- Credenziali di accesso pertinenti per DocFinance e Schedulatore.


### Configurazione come Servizio su Windows (Opzionale)

Per configurare lo script come servizio su Windows Server utilizzando NSSM:

1. Scarica e installa NSSM da [nssm.cc](https://nssm.cc/).
2. Esegui il seguente comando per installare il servizio:
   ```sh
   nssm install FileMoverDocFinance python.exe C:\path\to\script.py
   ```
3. Avvia il servizio:
   ```sh
   nssm start FileMoverDocFinance
   ```

## Licenza
Disponibile su licenza.

## Contatti

Per qualsiasi richiesta, contatta l'autore scrivendo a: g punto costantini at gmail punto com

  
**English:**
  
This repository contains an original Python script by Giovanni Costantini, Pesaro, designed to connect the "DocFinance (tm)" software by DocFinance S.r.l. (Reggio Emilia, Italy, https://www.docfinance.net/) with the "Schedulatore (tm)" software by Cariparma / Crédit Agricole Bank. This integration bridges the gap between these two systems, which are not natively integrated.

## Features

- **Folder Monitoring**: Uses the watchdog module to monitor specified folders in real-time.
- **Prefix-based File Movement**: Moves files based on predefined prefixes.
- **Extension-based File Movement**: Moves files based on predefined extensions.
- **Special Movement Rules**: Handles the movement of SEPA Credit Trans and SDD files, as well as RIBA presentation and supplier payment files.
- **Logging**: Utilizes TimedRotatingFileHandler to create a new log file each day, detailing file movements and any errors.
- **Windows Service Configuration**: Successfully configured as a service on Windows Server using NSSM (Non-Sucking Service Manager).

## Specifications

- **Python Version**: Python 3.x
- **Required Modules**: os, shutil, logging, configparser, watchdog, time
- **Configuration File**: config.ini
- **Log File**: file_mover.log

## Requirements

- Python 3.x
- Relevant access credentials for both DocFinance and Schedulatore.


### Windows Service Setup (Optional)

To configure the script as a service on Windows Server using NSSM:

1. Download and install NSSM from [nssm.cc](https://nssm.cc/).
2. Run the following command to install the service:
   ```sh
   nssm install FileMoverDocFinance python.exe C:\path\to\script.py
   ```
3. Start the service:
   ```sh
   nssm start FileMoverDocFinance
   ```

## License
Available under license

## Contatti

For further info, contact the author at g dot costantini at gmail dot com


