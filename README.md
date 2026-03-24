# LV3 Pandas und Wetterdaten

Dieses Repository begleitet die Arbeit mit `pandas` im Rahmen der Lehrveranstaltung.  
Es kombiniert einen kompakten Einstieg in die wichtigsten Grundideen von `pandas` mit einem einfachen, aber realistischen Beispiel auf Basis von Wetterdaten.

Im Zentrum stehen zwei Notebooks:

1. `10_minutes_to_pandas.ipynb` als strukturierter Einstieg in zentrale `pandas`-Konzepte
2. `import_weather_data_simple.ipynb` als kleines Praxisbeispiel mit echten Daten, Visualisierung und Export

## Ziel des Projekts

Ziel ist es, die grundlegenden Arbeitsweisen von `pandas` nicht nur isoliert kennenzulernen, sondern sie auch in einem zusammenhaengenden Ablauf anzuwenden:

- Daten einlesen
- Datenstrukturen verstehen
- Daten auswaehlen und bearbeiten
- Zeitreihen verarbeiten
- Ergebnisse visualisieren
- Ausgaben fuer die Weiterverwendung exportieren

Im Ordner `notebooks/` liegen dazu:

- `10_minutes_to_pandas.ipynb`
- `import_weather_data_simple.ipynb`
- Beispiel- und Exportdateien

Zusammen mit den Unterordnern `notebooks/data/` und `notebooks/plots/` entsteht so ein kleiner Lernpfad von den Grundlagen bis zu einem ersten anwendungsnahen Datensatz.

## Setup mit uv

Wenn das Projekt lokal neu aufgesetzt werden soll, kann der Ablauf im Terminal so aussehen:

```powershell
uv init
uv venv
.\.venv\Scripts\Activate.ps1
uv add pandas matplotlib openpyxl xlsxwriter ipykernel
```

Falls das Notebook direkt mit dem Projekt-Environment verbunden werden soll:

```powershell
uv run python -m ipykernel install --user --name 260324-lv3 --display-name "Python (260324-lv3)"
```

Danach kann Jupyter zum Beispiel so gestartet werden:

```powershell
uv run jupyter notebook
```

Alternativ kann direkt in VS Code mit dem Interpreter aus `.venv` gearbeitet werden.

## Abhaengigkeiten

Die Abhaengigkeiten werden ueber `uv` verwaltet und stehen in `pyproject.toml`.

Aktuell verwendet das Projekt unter anderem:

- `pandas`
- `matplotlib`
- `openpyxl`
- `xlsxwriter`
- `ipykernel`

## 10 Minutes to pandas

Das Notebook `notebooks/10_minutes_to_pandas.ipynb` orientiert sich an der bekannten pandas-Einfuehrung "10 minutes to pandas".  
Es dient als kompakte Lernstrecke und fuehrt Schritt fuer Schritt durch typische Grundlagen:

- Objekte erzeugen
- Daten ansehen
- Auswahl und Zugriff
- Werte setzen
- fehlende Daten
- Operationen
- Zeitreihen
- Plotten
- Speichern und Laden

Online-Dokumentation:

- pandas User Guide: <https://pandas.pydata.org/docs/user_guide/index.html>
- 10 Minutes to pandas: <https://pandas.pydata.org/docs/user_guide/10min.html>
- pandas Cheatsheet: <https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf>
- matplotlib Documentation: <https://matplotlib.org/stable/>
- matplotlib Cheatsheets: <https://matplotlib.org/cheatsheets/>

Dieses Notebook eignet sich gut, um zunaechst die Sprache von `Series`, `DataFrame`, Index, Auswahl, Gruppierung und Zeitreihen kennenzulernen, bevor mit echten Daten gearbeitet wird.

Der Anspruch ist dabei bewusst nicht Vollstaendigkeit, sondern ein klarer, schneller und nachvollziehbarer Einstieg.

## Wetterdaten-Beispiel

Das Notebook `notebooks/import_weather_data_simple.ipynb` zeigt einen kleinen End-to-End-Ablauf mit echten Wetterdaten.  
Hier wird sichtbar, wie sich die zuvor geuebten `pandas`-Grundlagen in einem einfachen Anwendungsszenario einsetzen lassen:

1. Konfiguration und Dateipfade festlegen
2. Stations-Metadaten laden und eine passende Station waehlen
3. Wetterdaten abrufen
4. JSON in ein `pandas.DataFrame` umwandeln
5. mehrere Wettergroessen gemeinsam plotten
6. Ergebnisse als Excel, PDF, JPG und HTML exportieren

Damit wird deutlich, dass `pandas` nicht nur mit kuenstlichen Uebungsdaten sinnvoll ist, sondern auch in einem kleinen realen Analysekontext gut eingesetzt werden kann.

Ein wichtiger technischer Punkt betrifft den Excel-Export:

- Excel unterstuetzt keine Datumswerte mit Zeitzonen
- deshalb wird vor `to_excel(...)` eine Kopie des DataFrames erzeugt
- dort werden timezone-behaftete Zeitstempel mit `tz_localize(None)` tz-unaware gemacht
- der Analyse-DataFrame bleibt dabei unveraendert

## Projektstruktur

```text
.
|-- .gitignore
|-- README.md
|-- main.py
|-- pyproject.toml
|-- uv.lock
`-- notebooks/
    |-- 10_minutes_to_pandas.ipynb
    |-- import_weather_data_simple.ipynb
    |-- example_pandas.csv
    |-- example_pandas.xlsx
    |-- data/
    `-- plots/
```

## .gitignore

Die `.gitignore` ist absichtlich auf dieses Lernprojekt abgestimmt. Sie schliesst vor allem Dinge aus, die nicht ins Repository gehoeren:

- Python-Artefakte wie `__pycache__/`, `*.pyc`, Build-Ordner und `*.egg-info`
- die virtuelle Umgebung `.venv`
- erzeugte Exportdateien wie `*.xlsx`, `*.pdf`, `*.html`, `*.jpg` und `*.csv`

Das ist fuer die Arbeit im Kurs praktisch, weil die eigentlichen Notebooks versioniert bleiben, erzeugte Ausgaben und temporaere Umgebungsdateien aber nicht dauernd als Git-Aenderungen auftauchen.

## Kurz gesagt

Dieses Repository verbindet einen kompakten `pandas`-Einstieg mit einem ueberschaubaren Praxisbeispiel.  
Zunaechst werden die grundlegenden Konzepte in `10_minutes_to_pandas.ipynb` aufgebaut, anschliessend werden sie im Wetter-Notebook an realen Daten angewendet.
