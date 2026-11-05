## Übergabe: NotebookLM-CLI + Skill für Claude Code

### Ziel
NotebookLM per CLI und Skill in Claude Code nutzen. Der Skill soll zusätzlich im iVault liegen.

### Recherche (Websuche, nicht selbst geprüft)
- **Empfehlung:** `teng-lin/notebooklm-py`, https://github.com/teng-lin/notebooklm-py
  - Inoffizielle Python-API plus CLI für NotebookLM, MIT-Lizenz.
  - Nutzt undokumentierte Google-APIs und kann bei Google-Änderungen brechen.
  - Enthält eine `SKILL.md` für Claude Code und Codex.
- **Weitere Skills:**
  - `PleasePrompto/notebooklm-skill`: Browser-Automation, Antworten mit Quellenangaben.
  - `claude-world/notebooklm-skill`: Pipeline von Recherche bis Content, mit MCP-Server und CLI.
  - `robonuggets/notebooklm-skill`: Quellen automatisch hinzufügen, Slide-Decks, Auth-Cookies automatisch erneuern.
  - `nlm` auf MCP Market: https://mcpmarket.com/tools/skills/notebooklm-cli-integration

### Erledigt
- Im Cloud-Container installiert: `notebooklm-py` 0.8.6 und der Skill (`notebooklm skill install`).
  - Der Container ist temporär, die Installation geht mit der Session verloren.
  - Ein Google-Login war dort nicht möglich, es gibt keinen Browser. Es wurde nichts gegen echte Notebooks getestet.
- Der Skill ist im Repo `km9xdx9qkv-wq/claude-code` unter `.claude/skills/notebooklm/SKILL.md` committet.
  - Branch: `claude/peaceful-goldberg-xe0tb0`
  - Draft-PR: https://github.com/km9xdx9qkv-wq/claude-code/pull/2

### Offen: Skill im iVault ablegen
- Dein Mac heißt `MacBook-Pro-von-Andre.fritz.box`. Die Ordner `iVault` und `Claude_Code` stehen in Remote Control, werden Cloud-Sessions aber nicht angeboten.
- Desktop Commander meldet das MacBook als „Online" (Geräte-ID `32e03ab5-9450-4531-84e1-fb9dcfe9af71`). Die Suche nach „iVault" lief aber in einen Timeout. `list_directory` auf `/Users` kam nicht zurück.
- Mögliche Ursachen: Mac im Ruhezustand, Desktop-Commander-App hängt, oder die Claude-App auf dem Mac ist veraltet.
- Im iVault wurde nichts angelegt oder geändert.
- Regel: Vor jeder Änderung im iVault zuerst `iVault/CLAUDE.md` lesen. Das ist noch nicht passiert.
- Noch unklar: In welchen iVault-Ordner Skills gehören.

### Nächste Schritte
1. Mac aufwecken und Desktop Commander öffnen.
2. `iVault/CLAUDE.md` lesen.
3. Skill aus PR #2 (`.claude/skills/notebooklm/SKILL.md`) oder per `notebooklm skill install` in den passenden iVault-Ordner legen.
4. Lokal einrichten, falls noch nicht geschehen:
   - `pip install "notebooklm-py[browser]"`
   - `playwright install chromium`
   - `notebooklm skill install`
   - `notebooklm login`
