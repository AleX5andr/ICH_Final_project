📊 **Datenquellen & Datenimport**

Dieses Projekt verwendet mehrere Datensätze aus Google Sheets, die aus Datenschutz- und Sicherheitsgründen nicht direkt im Repository gespeichert werden.
Die Daten stammen aus dem CRM-System der Online-Programmierschule und umfassen:

📞 calls – Informationen zu Anrufen

👥 contacts – Kontaktinformationen

📄 deals – Leads und Verkaufsprozesse

💰 spend – Marketing- und Werbekosten

Alle Dateien werden während der Analyse automatisch aus Google Sheets geladen.



🔗 **Links zu den verwendeten Google Sheets**

| Name     | Beschreibung         | Link |
|----------|-----------------------|------|
| calls    | Anrufaktivität       | https://docs.google.com/spreadsheets/d/1R0RGTCA13llyrsSnbEHNsJZqYhELlz8q/edit?usp=sharing |
| contacts | Kontakte             | https://docs.google.com/spreadsheets/d/1yBklBNwMNmmxxdGR11QcqxuH4QX82vNo/edit?usp=sharing |
| deals    | Verkaufsprozesse     | https://docs.google.com/spreadsheets/d/1hGoe5yHfmBKZ_XRd_7jTbTQ1vflT7R1G/edit?usp=sharing |
| spend    | Werbeausgaben        | https://docs.google.com/spreadsheets/d/1ZNU4Ll0fkDf_BOqn44SXvrUod8Y-eMjM/edit?usp=sharing |

(Die Daten enthalten keine personenbezogenen Informationen.)


📥 **Datenimport in Google Colab**

Die folgenden Python-Snippets zeigen, wie die Daten im Projekt geladen werden.
Die Google-Sheets-URLs werden automatisch in direkte Download-Links umgewandelt.


🔧 **Beispielcode zum Laden der Daten**

```python
calls = (
    "https://docs.google.com/spreadsheets/d/1R0RGTCA13llyrsSnbEHNsJZqYhELlz8q/"
    "edit?usp=sharing&ouid=101122644310264117380&rtpof=true&sd=true"
)
contacts = (
    "https://docs.google.com/spreadsheets/d/1yBklBNwMNmmxxdGR11QcqxuH4QX82vNo/"
    "edit?usp=sharing&ouid=101122644310264117380&rtpof=true&sd=true"
)
deals = (
    "https://docs.google.com/spreadsheets/d/1hGoe5yHfmBKZ_XRd_7jTbTQ1vflT7R1G/"
    "edit?usp=sharing&ouid=101122644310264117380&rtpof=true&sd=true"
)
spend = (
    "https://docs.google.com/spreadsheets/d/1ZNU4Ll0fkDf_BOqn44SXvrUod8Y-eMjM/"
    "edit?usp=sharing&ouid=101122644310264117380&rtpof=true&sd=true"
)
```


🔧 **Programmatischer Import aller Dateien**

```python
dfs = {}
for name, url in files.items():
    try:
        # ID der Google-Sheets-Datei extrahieren
        url = url.split("/d/")[1].split("/")[0]
        download_url = f"https://drive.google.com/uc?export=download&id={url}"

        # Datei laden
        dfs[name] = pd.read_excel(
            download_url,
            dtype={"Id": "string", "CONTACTID": "string", "Contact Name": "string"}
        )
        
        globals()[name] = dfs[name]
        print(f"'{name.capitalize()}' loaded.")

    except Exception as e:
        print(f"Error uploading file '{name.capitalize()}': {e}")

```


📝 **Hinweis**

Dieses Repository enthält bewusst keine originalen Datendateien, sondern nur die Links sowie die Ladelogik.
Dies entspricht bewährten Methoden zur sicheren Verarbeitung sensibler Geschäftsdaten.


🎯 **Zweck dieses Dokuments**

Dieses README_DATA.md dient dazu:

- die Datenquellen transparent zu dokumentieren

- die Struktur und Herkunft der Daten zu erklären

- wiederholbare Datenimporte sicherzustellen

- das Projekt auditierbar und nachvollziehbar zu machen
