# CLAUDE.md

Repo: Fork des öffentlichen Claude-Code-Repos (Plugins, Beispiele, Issue-Automatisierung) plus eigene Ergänzungen. Es enthält keinen Quellcode der CLI selbst.

## Struktur
- `plugins/`: Offizielle Beispiel-Plugins. Jedes hat `.claude-plugin/plugin.json` und `commands/`, teils `agents/`, `skills/`, `hooks/`. Übersicht in `plugins/README.md`.
- `.claude/commands/`: Projekt-Slash-Commands (`commit-push-pr`, `dedupe`, `triage-issue`).
- `.claude/skills/notebooklm/`: Skill für `notebooklm-py` (NotebookLM per CLI).
- `scripts/`: TypeScript- und Shell-Skripte für die GitHub-Workflows (Issue-Triage, Duplikate, Lifecycle).
- `.github/workflows/`: Workflows für Issue-Automatisierung und `claude.yml`.
- `examples/`: Beispielkonfigurationen.
- `docs/notebooklm-handover.md`: Übergabe-Notiz zum NotebookLM-Setup.

## NotebookLM-Skill
Lokal einrichten (der Google-Login braucht einen Browser, im Cloud-Container nicht möglich):
```bash
pip install "notebooklm-py[browser]"
playwright install chromium
notebooklm skill install
notebooklm login
```

## iVault
Der iVault liegt auf dem Mac des Users, nicht in diesem Repo und nicht im Cloud-Container. Er ist nur über Desktop Commander oder Remote Control erreichbar, sofern der Mac online ist. Vor jeder Änderung im iVault zuerst `iVault/CLAUDE.md` lesen. Erst danach etwas anlegen oder ändern.

Ist der Mac nicht erreichbar oder die Datei nicht auffindbar: nichts im iVault anlegen oder ändern, stoppen und den User fragen.

## Arbeitsweise
- Auf dem vorgegebenen Feature-Branch arbeiten, nicht auf `main`.
- Vor neuer Arbeit prüfen, ob der PR des Branches schon gemerged ist. Falls ja, den Branch auf `origin/main` neu aufsetzen, bevor etwas darauf landet.
- Danach pushen und einen Draft-PR öffnen, falls kein offener PR für den Branch existiert. Ein gemergter oder geschlossener PR zählt nicht.
- Antworten an den User und Notizen auf Deutsch. Commit-Messages, PR-Titel und -Texte sowie Code-Kommentare auf Englisch, wie in der bisherigen Historie.
