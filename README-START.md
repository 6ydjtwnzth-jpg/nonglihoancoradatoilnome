# Percorso — kit di partenza per Claude Code

## Cosa c'è dentro
- `CLAUDE.md` — memoria di progetto (sotto le 200 righe, come consigliato dalla documentazione).
- `KICKOFF_PROMPT.md` — il prompt da incollare nella prima sessione.
- `docs/` — arte, UX, game design, architettura, roadmap.
- `.claude/agents/` — 7 sub-agenti specializzati ("robot"): art-director, ux-designer, physics-engineer, level-designer, audio-designer, qa-playtester, perf-a11y-auditor.
- `.claude/skills/` — `art-review` e `level-check`.
- `public/robots.txt` — da adattare quando c'è un dominio.
- `prototype/percorso.html` — il prototipo attuale, riferimento di feel e fisica.

## Installazione di Claude Code
Metodo consigliato (installer nativo, si aggiorna da solo):
- macOS / Linux / WSL: `curl -fsSL https://claude.ai/install.sh | bash`
- Windows PowerShell: `irm https://claude.ai/install.ps1 | iex`
- Alternative: Homebrew (`brew install --cask claude-code`), WinGet (`winget install Anthropic.ClaudeCode`).
Poi: `claude --version`, `claude` nella cartella del progetto, accedi con il tuo account Claude o una chiave API.
Documentazione: https://code.claude.com/docs (indice completo: https://code.claude.com/docs/llms.txt).

## Come usare i pezzi (cosa serve a cosa)
- **CLAUDE.md**: regole sempre attive. Tienilo corto; il resto sta nei doc.
- **Skills** (`.claude/skills/`): procedure caricate quando servono (revisione arte, verifica livelli).
- **Subagenti** (`.claude/agents/`): specialisti con contesto isolato. Usali per revisioni indipendenti.
- **Hooks**: automazioni su eventi (es. lint/typecheck dopo ogni modifica). Configurali con `/hooks` e la guida ufficiale.
- **MCP**: collegamenti a servizi esterni. Utili qui: un MCP di browser (es. Playwright) per screenshot e test su viewport mobile, Figma per le specifiche di design, GitHub per issue e PR. Verifica comandi e nomi aggiornati nella documentazione MCP prima di installare.
- **Plan mode**: usalo sempre per task su più file. Tieni i permessi manuali nella prima sessione.
- **Permessi**: configura allow/deny con `/permissions` (consenti i comandi `npm run`, nega la lettura di `.env`).

## Strumenti consigliati fuori da Claude Code
- **Arte/UX:** Figma (style tile, icone, prototipo cliccabile), una raccolta di riferimenti (Are.na/Pinterest), un tool per palette e contrasto.
- **Audio:** una DAW (Ableton, Reaper o simili) e Synplant 2 se vuoi il suono originale del preset "Fragile Hearts": esportare le tracce e usarle come sample/stem accanto alla sintesi Web Audio.
- **Test su dispositivo:** un iPhone e un Android di fascia media reali, collegati per il debug remoto del browser. Il feel dell'input non si valida su emulatore.
- **Analisi:** Lighthouse, il profiler del browser e un registratore di schermo per i playtest.

## Ordine consigliato per la prima settimana
1. Giorno 1: incolla il prompt, ottieni audit del prototipo e domande aperte.
2. Giorni 2-3: scegli le direzioni artistiche dagli style tile; chiudi i wireflow.
3. Giorno 4: approva le ADR e lo scaffolding.
4. Giorno 5: primo vertical slice (un livello per mondo) con arte e audio finali, da giocare su un telefono vero.
