# Claude Code — Prosjektkonfigurasjon

## Filsystem-tilgang via MCP

Dette prosjektet er konfigurert med en MCP-server som gir Claude Code tilgang
til å lese og navigere filer på den lokale maskinen.

### Hva er satt opp

- **Server**: `@modelcontextprotocol/server-filesystem`
- **Konfigurasjonsfil**: `.claude/settings.json`
- **Tillatte mapper**: `/home/user` (og alle undermapper)

### Slik fungerer det

Når du åpner Claude Code i dette prosjektet, startes MCP-serveren automatisk
via `npx`. Claude Code kan da bruke verktøy som:

- `list_directory` — vise innholdet i en mappe
- `read_file` — lese innholdet i en fil
- `search_files` — søke etter filer med mønster
- `get_file_info` — hente metadata om en fil

### Endre tillatte mapper

For å gi tilgang til flere mapper, legg til stier i `args`-listen i
`.claude/settings.json`:

```json
"args": ["-y", "@modelcontextprotocol/server-filesystem", "/home/user", "/tmp"]
```

### Sikkerhetsmerknad

MCP-serveren kan lese (og med de riktige verktøyene skrive) filer i de
tillatte mappene. Begrens tilgangen til mapper som inneholder sensitiv
informasjon.
