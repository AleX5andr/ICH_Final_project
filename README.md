🧠 **CRM-Datenanalyse – Abschlussprojekt**

Datenbereinigung und umfassende Analyse von CRM-Daten einer Online-Programmierschule mit Python zur Steigerung der Marketing- und Vertriebseffizienz.

Dieses Projekt wurde im Rahmen meiner Abschlussarbeit im Bereich Data Analytics (itcareerhub.de) durchgeführt und umfasst den vollständigen Analyseprozess:
von der Datenbereinigung über explorative Analyse bis hin zur Produktanalyse und Hypothesenentwicklung.

---

📂 **Repository-Struktur**

```python
ICH_Final_project/
│
├── notebooks/
│     ├── 01_data_cleaning.ipynb
│     ├── 02_eda.ipynb
│     └── 03_analysis.ipynb
│
├── data/
│     ├── README_DATA.md
│     └── product_analytics.xlsx
│
├── powerbi/
│     └── dashboard.pbix
│
└── README.md

```

---

📘 **Notebooks (Google Colab)**

```python
| Notebook                   | Beschreibung                                                                                                 | Link                                           |
| -------------------------- | ------------------------------------------------------------------------------------------------------------ | ---------------------------------------------- |
| **01_data_cleaning.ipynb** | Datenbereinigung, Typkonvertierung, Behandlung fehlender Werte, deskriptive Statistik                        | https://github.com/AleX5andr/ICH_Final_project/blob/main/notebooks/01_data_cleaning.ipynb |
| **02_eda.ipynb**           | Zeitreihenanalyse, Kampagnenanalyse, Vertriebsanalyse, Zahlungs- und Produktanalyse, geografische Auswertung | https://github.com/AleX5andr/ICH_Final_project/blob/main/notebooks/02_eda.ipynb |
| **03_analysis.ipynb**      | Produktanalyse, Unit Economics, Metrikbaum, Hypothesenentwicklung und Testmethodik                           | https://github.com/AleX5andr/ICH_Final_project/blob/main/notebooks/03_analysis.ipynb |

```

---

📊 **Datenquellen (Google Sheets)**

Die Daten werden aus dem CRM-System exportiert und befinden sich aufgrund von Datenschutzrichtlinien nicht direkt im Repository.
Stattdessen werden sie aus Google Sheets in Google Colab geladen.

---

🔗 **Google Sheets Dateien**

```python
| Dataset  | Beschreibung      | Link                                                                                                                                                                                   |
| -------- | ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| calls    | Anrufaktivität    | [https://docs.google.com/spreadsheets/d/1R0RGTCA13llyrsSnbEHNsJZqYhELlz8q/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1R0RGTCA13llyrsSnbEHNsJZqYhELlz8q/edit?usp=sharing) |
| contacts | Kontakte          | [https://docs.google.com/spreadsheets/d/1yBklBNwMNmmxxdGR11QcqxuH4QX82vNo/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1yBklBNwMNmmxxdGR11QcqxuH4QX82vNo/edit?usp=sharing) |
| deals    | Verkaufsprozesse  | [https://docs.google.com/spreadsheets/d/1hGoe5yHfmBKZ_XRd_7jTbTQ1vflT7R1G/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1hGoe5yHfmBKZ_XRd_7jTbTQ1vflT7R1G/edit?usp=sharing) |
| spend    | Marketingausgaben | [https://docs.google.com/spreadsheets/d/1ZNU4Ll0fkDf_BOqn44SXvrUod8Y-eMjM/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1ZNU4Ll0fkDf_BOqn44SXvrUod8Y-eMjM/edit?usp=sharing) |

```

Zusätzliche Produktanalyse (Unit Economics) befindet sich in:
📄 /data/product_analytics.xlsx

---

📥 **Datenimport in Google Colab**

```python
files = {
    "calls": calls,
    "contacts": contacts,
    "deals": deals,
    "spend": spend,
}

dfs = {}

for name, url in files.items():
    try:
        # ID der Google-Sheets-Datei extrahieren
        file_id = url.split("/d/")[1].split("/")[0]
        download_url = f"https://drive.google.com/uc?export=download&id={file_id}"

        # Datei laden
        df = pd.read_excel(
            download_url,
            dtype={"Id": "string", "CONTACTID": "string", "Contact Name": "string"}
        )

        dfs[name] = df
        globals()[name] = df

        print(f"{name.capitalize()} loaded.")

    except Exception as e:
        print(f"Error loading file '{name}': {e}")

```

---

📈 **Analyseübersicht**

1️⃣ Datenbereinigung

- Entfernen von Duplikaten

- Behandlung fehlender Werte

- Datentypkorrekturen

- Deskriptive Statistik

2️⃣ Explorative Datenanalyse (EDA)

- Zeitreihen: Deals, Calls, Abschlussdauer

- Kampagnen-Performance

- Analyse der Marketingquellen

- Owner- und Teamperformance

- Analyse der Zahlungsarten

- Produktperformance

- Geografische Analyse

3️⃣ Produktanalyse & Hypothesen

- Unit Economics pro Produkt

- Identifikation von Wachstumspunkten

- Aufbau eines Metrikbaums

- Formulierung wachstumsorientierter Hypothesen

- Beschreibung einer 2-wöchigen Testmethodik

---

📊 **Power BI Dashboard**

Der interaktive Dashboard befindet sich unter:
📁 /powerbi/dashboard.pbix

Er enthält:

- Conversion Funnel

- Kampagnenvergleich

- Owner-Performance

- Produkt-Insights

- Unit Economics (visuell dargestellt)

---

🧑‍💻 **Autor**

Oleksandr Muntian

Data Analyst

Python • SQL • MongoDB • Power BI • Tableau

LinkedIn: www.linkedin.com/in/oleksandr-muntian-6762692b1
