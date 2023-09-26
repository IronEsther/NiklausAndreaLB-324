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

- repo: https://github.com/pre-commit/pre-commit-hooks
  rev: v2.0.0
  hooks:
  - id: check-yaml
  - id: check-added-large-files
  - id: mixed-line-ending
    args:
    - --fix=auto
  - id: trailing-whitespace
  - id: flake8



- repo: local
  hooks:
  -   id: needs-hash
      name: commit message needs issues
      language: pygrep
      entry: '#\d+'
      args: [--multiline, --negate]
      stages: [commit-msg]

  -   id: pytest-check
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

## Aufgabe 4
Erklären Sie hier, wie Sie das Passwort aus Ihrer lokalen `.env` auf Azure übertragen.
