# LB 324

## Aufgabe 2
Installierung von `pre-commit` auf `python`:
1. In der cmd zum Ordner navigieren und pre-commit installieren:
```cmd
pip install pre-commit
```
Pre-commit wird dadurch auf dem Gerät installiert. 
<a href="https://cdn.discordapp.com/attachments/1059541999633580154/1156212863413788783/precommit-install.png?ex=651426a4&is=6512d524&hm=d15ae164d46d4326608062f3b354cf7202931bbc00d1d6bc93f16d85e898a482&" title="precommit-installation"><img src="{image-url}" alt="  " /></a>

2. Im requirements.txt `pre-commit` auf einer neuen Zeile hinzufügen. 
3. Ein neues File namens `.pre-commit-config.yaml` erstellen.
   --> Man kann auch per `pre-commit sample-config`eine einfache Vorlage generieren lassen.
4. Im File `.pre-commit-config.yaml` folgender Code kopieren:

 ```.yaml
repos:
  - repo: https://github.com/ambv/black
    rev: 23.7.0
    hooks:
      - id: black
        language_version: python3.11
        stages: [push]

  - repo: local
    hooks:
      - id: pytest-check
        stages: [push]
        types: [python]
        name: pytest-check
        entry: python -m pytest
        language: system
        pass_filenames: false
        always_run: true
 ```
5. Den Git Hook Script installieren:
   - im cmd `pre-commit install` einfügen und ausführen, um die git hook scipts zu installieren
Das pre-commit wird nun automatisch auf git commit laufen. :D

Wenn man Änderungen nun speichern will, kann man zur Konsole gehen, zum directory des Repositories (also `cd C:\Users\...`) und dort dann `git commit` oder `git push` oder `git pull` eingeben. (Kommt drauf an was man machen will) Wenn man dies gemacht hat, dann wird der Code getestet und wenn er läuft, auch hochgeladen.

## Aufgabe 4
niklausandrealb-324.azurewebsites.net

Auf Azure muss man auf `Konfiguration` navigieren. Dann muss man auf `Anwendungseinstellung hinzufügen` klicken und dort den Benutzernamen, also in diesem Fall `PASSWORD` und das Password im anderen Feld eingeben. Nun kann man dies speichern und aktualisieren.
