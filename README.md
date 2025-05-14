# Schedulatore Cariparma / Crédit Agricole Bank to DocFinance Integration Script

(IT) Script Python per connettere DocFinance™ con Schedulatore™ Cariparma / Crédit Agricole Bank. Monitora cartelle, sposta file, e può essere un servizio Windows con NSSM. Include un'interfaccia web per monitorare l'attività del file mover e i log.

(EN) Python script to connect DocFinance™ with Schedulatore™ Cariparma / Crédit Agricole Bank. Monitors folders, moves files, and can be a Windows service via NSSM. Includes a web interface for monitoring the file mover's activity and logs.

**Italian:**

# Script di Integrazione tra DocFinance e Schedulatore Cariparma / Crédit Agricole Bank

Questo repository contiene uno script Python originale progettato da Giovanni Costantini, Pesaro per connettere il software DocFinance™ di DocFinance S.r.l. (Reggio Emilia, Italia, https://www.docfinance.net/) con il software Schedulatore™ di Cariparma / Crédit Agricole Bank. Questa integrazione colma il divario tra questi due sistemi, che non sono integrati nativamente.

## Funzionalità

- **Monitoraggio delle Cartelle**: Scansiona periodicamente le cartelle specificate.
- **Spostamento Basato sui Prefissi**: Sposta i file in base ai prefissi predefiniti.
- **Spostamento Basato sulle Estensioni**: Sposta i file in base alle estensioni predefinite.
- **Regole di Spostamento Speciali**: Gestisce lo spostamento dei file SEPA Credit Trans ed SDD, nonché la Presentazione RIBA e il pagamento riba fornitori.
- **Logging**: Utilizza TimedRotatingFileHandler per creare un nuovo file di log ogni giorno, registrando dettagliatamente le attività di spostamento dei file e gli eventuali errori.
- **Configurazione come Servizio su Windows**: Configurato con successo come servizio su Windows Server tramite NSSM (Non-Sucking Service Manager).
- **Interfaccia Web**: Fornisce un'interfaccia web per monitorare l'attività del file mover e i log, inclusa la visualizzazione dei log, il monitoraggio degli errori e l'esportazione CSV dei dati di attività.

## Specifiche

- **Versione Python**: Python 3.x
- **Moduli Richiesti**: os, shutil, logging, configparser, time, argparse, pathlib, Flask
- **File di Configurazione**: config.ini
- **File di Log**: file_mover.log
- **Framework Interfaccia Web**: Flask

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

### Configurazione Interfaccia Web (Opzionale)

Per configurare l'interfaccia web:

1.  Installa i pacchetti Python richiesti:
    ```sh
    pip install flask
    ```
2.  Esegui lo script `install_web_service.py` per installare l'interfaccia web come servizio Windows.
3.  Accedi all'interfaccia web in un browser all'indirizzo `http://localhost:9999`.

## Configurazione

Il file `config.ini` contiene le seguenti sezioni:

*   `[paths]`: Specifica la cartella di origine da monitorare.
*   `[filters]`: Definisce le cartelle di destinazione per diversi tipi di file in base ai prefissi.
*   `[extensions]`: Definisce le cartelle di destinazione per diversi tipi di file in base alle estensioni.
*   `[source_to_destination]`: Definisce mappature specifiche da origine a destinazione per determinati tipi di file.
*   `[options]`: Configura `move_delay`, `log_level` e `scan_interval`.

Esempio di sezione `config.ini`:

```ini
[paths]
source_folder = E:\TeamSystem Software\docfinance-frontiera\schedulatore\RICEZIONE\INFORMATIVI

[filters]
RH = E:\TeamSystem Software\docfinance-frontiera\01\SFNGW\APP\FOREMONEY\CONTI\RX
```

## Licenza

Software proprietario, disponibile su licenza.

## Contatti

Per qualsiasi richiesta, contatta l'autore scrivendo a: g punto costantini chiocciola gmail punto com

**English:**

# Integration Script between DocFinance and Schedulatore Cariparma / Crédit Agricole Bank

This repository contains an original Python script by Giovanni Costantini, Pesaro, designed to connect the DocFinance™ software by DocFinance S.r.l. (Reggio Emilia, Italy, https://www.docfinance.net/) with the Schedulatore™ software by Cariparma / Crédit Agricole Bank. This integration bridges the gap between these two systems, which are not natively integrated.

## Features

- **Folder Monitoring**: Periodically scans the specified folders.
- **Prefix-based File Movement**: Moves files based on predefined prefixes.
- **Extension-based File Movement**: Moves files based on predefined extensions.
- **Special Movement Rules**: Handles the movement of SEPA Credit Trans and SDD files, as well as RIBA presentation and supplier payment files.
- **Logging**: Utilizes TimedRotatingFileHandler to create a new log file each day, detailing file movements and any errors.
- **Windows Service Configuration**: Successfully configured as a service on Windows Server using NSSM (Non-Sucking Service Manager).
- **Web Interface**: Provides a web interface for monitoring the file mover's activity and logs, including log viewing, error monitoring, and CSV export of activity data.

## Specifications

- **Python Version**: Python 3.x
- **Required Modules**: os, shutil, logging, configparser, time, argparse, pathlib, Flask
- **Configuration File**: config.ini
- **Log File**: file_mover.log
- **Web Interface Framework**: Flask

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

### Web Interface Setup (Optional)

To set up the web interface:

1.  Install the required Python packages:
    ```sh
    pip install flask
    ```
2.  Run the `install_web_service.py` script to install the web interface as a Windows service.
3.  Access the web interface in a browser at `http://localhost:9999`.

## Configuration

The `config.ini` file contains the following sections:

*   `[paths]`: Specifies the source folder to monitor.
*   `[filters]`: Defines the destination folders for different file types based on prefixes.
*   `[extensions]`: Defines the destination folders for different file types based on extensions.
*   `[source_to_destination]`: Defines specific source to destination mappings for certain file types.
*   `[options]`: Configures the `move_delay`, `log_level`, and `scan_interval`.

Example `config.ini` section:

```ini
[paths]
source_folder = E:\TeamSystem Software\docfinance-frontiera\schedulatore\RICEZIONE\INFORMATIVI

[filters]
RH = E:\TeamSystem Software\docfinance-frontiera\01\SFNGW\APP\FOREMONEY\CONTI\RX
```

## License

Proprietary software, available under license

## Contatti

For further info, contact the author at g dot costantini at gmail dot com
