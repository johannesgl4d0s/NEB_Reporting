# NEB Reporting Automation

Dieses Repository enthält ein Python-Skript und ein Jupyter Notebook zur automatisierten Erstellung von Netzbetreiber-Berichten (NEB-Berichte) auf Basis einer Excel-Datei und eines Word-Templates. Die generierten Reports werden sowohl lokal als auch auf einem SharePoint abgelegt.

---

## Projektstruktur

```
NEB_Reporting/
├── environment.yml           # Conda-Umgebungsdefinition
├── Bericht_NB_erzeugen.ipynb # Jupyter Notebook zur interaktiven Ausführung
└── README.md                 # Diese Datei
```

---

## Installation

### 1. Repository klonen
```bash
git clone https://github.com/johannesgl4d0s/NEB_Reporting.git
cd NEB_Reporting
```

### 2. Conda-Umgebung erzeugen
```bash
conda env create -f environment.yml
```

### 3. Umgebung aktivieren
```bash
conda activate neb_reporting
```


---

## Environment-Datei (`environment.yml`)

```yaml
name: neb_reporting
channels:
  - defaults
dependencies:
  - python=3.9
  - pandas
  - openpyxl
  - python-docx
  - pywin32
  - office365-rest-python-client
  - msal
  - pip
  - pip:
    - docx2pdf
    - jupyterlab
```

---

## Konfiguration

Passe in `neb_reporting.py` bzw. `Bericht_NB_erzeugen.ipynb` folgende Variablen an:

- **`report_monat`**: Berichtsmonat im Format `YYYY-MM`  
- **`EXCEL_PATH`**: Pfad zur Excel-Datei mit den Daten  
- **`TEMPLATE_PATH`**: Pfad zum Word-Template (`.docx`)  
- **`OUT_DIR`**: Ausgabe-Verzeichnis für die generierten Dateien  

**SharePoint-Konfiguration**:  
- `TENANT_ID`, `CLIENT_ID`, `CLIENT_SECRET` für die Azure-AD App  
- SharePoint Site-URL (z.B. `https://aggmag.sharepoint.com/sites/NEB`)

---

## Ausführung

### Jupyter Notebook
```bash
jupyter lab
```
Öffne `Bericht_NB_erzeugen.ipynb` und führe die Zellen schrittweise aus.


Die Berichte werden im lokalen `OUT_DIR` gespeichert und anschließend automatisch in die jeweiligen SharePoint-Ordner hochgeladen.

---

## License

Dieses Projekt ist unter der MIT-Lizenz veröffentlicht.
