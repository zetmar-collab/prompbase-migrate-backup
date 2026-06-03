# PrompBase — migracja kopii zapasowej do v2.5

Skrypt Python dopasowujący starą kopię zapasową PrompBase (`prompbase-backup-*.json`) do formatu **PrompBase v2.5** i zapisujący wynik jako `nowe.json` gotowy do importu.

## Wymagania

- Python 3.10+
- Sklonowane repozytorium [PrompBase-Python](https://github.com/zetmar-collab/PrompBase-Python) (skrypt importuje `promptbase.py` z głównego katalogu projektu)

## Instalacja

```bash
git clone https://github.com/zetmar-collab/PrompBase-Python.git
cd PrompBase-Python
```

Skopiuj `migrate_backup_to_nowe.py` do folderu `scripts/` w tym repozytorium (lub pobierz sam plik i umieść go w `scripts/`).

## Użycie

1. Umieść kopię zapasową w folderze `Prompty/`, np. `Prompty/prompbase-backup-20260603-1535.json`

2. Uruchom z katalogu głównego PrompBase-Python:

```bash
python scripts/migrate_backup_to_nowe.py
```

Wynik: `Prompty/nowe.json` — import w aplikacji: **Plik → Przywróć z JSON** lub **Szybki import JSON**.

### Opcje

```bash
python scripts/migrate_backup_to_nowe.py --input Prompty/moja-kopia.json --output Prompty/nowe.json
python scripts/migrate_backup_to_nowe.py --keep-source   # nie usuwa pliku wejściowego
```

## Co robi skrypt

- Normalizuje placeholdery (`[temat]` → `[TEMAT]`, spacje w nawiasach → `_`)
- Mapuje nazwy modeli (`ChatGPT` → `GPT-5.5`, `Claude` → `Claude Sonnet 4.6`)
- Czyści znane artefakty w treści promptów
- Zachowuje ustawienia: motyw, foldery chmury, checklistę, ID promptów

## Autor

Marek Zettel — [PrompBase](https://github.com/zetmar-collab/PrompBase-Python)

## Licencja

Ten sam projekt co PrompBase-Python (repozytorium nadrzędne).
