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
Der iVault liegt auf dem Mac des Users, nicht in diesem Repo. Vor jeder Änderung im iVault zuerst `iVault/CLAUDE.md` lesen. Erst danach etwas anlegen oder ändern.

## Arbeitsweise
- Auf dem vorgegebenen Feature-Branch arbeiten, nicht auf `main`.
- Nach dem Push einen Draft-PR öffnen, falls noch keiner offen ist.
- Ist der PR des Branches schon gemerged, den Branch auf `origin/main` neu aufsetzen, bevor neue Arbeit darauf landet.
- Antworten und Notizen auf Deutsch.
