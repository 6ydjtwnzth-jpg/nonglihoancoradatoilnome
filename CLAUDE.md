# Percorso — gioco di fisica, dreamy

Gioco mobile-first: l'utente disegna linee col dito, la pallina cade da A e deve arrivare a B.
Due mondi (space, lava), 40 livelli, punteggio basato sull'inchiostro risparmiato.
Il prototipo funzionante è `prototype/percorso.html` (un solo file, vanilla JS): è un riferimento, non la base finale.

## Priorità (in ordine)
1. **Feel**: il tratto segue il dito senza ritardo percepibile; fisica credibile e stabile a 60 fps su telefoni medi.
2. **Direzione artistica**: coerenza, morbidezza, atmosfera dreamy. Ogni pixel è una scelta. Vedi `docs/ART_DIRECTION.md`.
3. **UX**: zero attrito, zero testo non necessario, pollice-friendly. Vedi `docs/UX_PRINCIPLES.md`.
4. **Correttezza dei livelli**: ogni livello deve essere dimostrabilmente risolvibile.
5. Pulizia del codice e test.

## Come lavorare
- Per ogni task che tocca più di un file: **plan mode prima**, poi implementa a piccoli passi.
- Prima di cambiare estetica o UX leggi i doc in `docs/` e usa gli agenti in `.claude/agents/`.
- Non inventare scelte artistiche: se manca una decisione, proponi 2-3 opzioni con mockup e chiedi.
- Ogni commit: lint + typecheck + test verdi. Per ogni modifica visiva allega screenshot (mobile, 390x844).
- Nessuna nuova dipendenza senza motivazione (peso, manutenzione). Budget in ARCHITECTURE.md.
- Lingua: UI senza testo (icone); doc e copy in italiano; codice, commenti e commit in inglese.

## Comandi (da completare dopo lo scaffolding)
`npm run dev` · `build` · `test` (unit) · `e2e` (Playwright) · `lint` · `typecheck` · `levels:check` (valida e risolve i livelli in headless)

## Regole non negoziabili
- Fisica a **timestep fisso** (1/480 s, accumulatore): mai legata al frame rate.
- Dati dei livelli in file validati da schema, mai dentro il codice di rendering.
- Ogni animazione rispetta `prefers-reduced-motion`.
- Audio: parte solo dopo un gesto utente, sempre disattivabile, volume mai alto di default.
- Storage dietro un'interfaccia, sempre con try/catch.
- Colori e misure solo da design token (`src/theme/tokens.ts`), mai hardcoded nei componenti.
- Accessibilità: contrasto, target tocco ≥ 44 px, niente significato affidato al solo colore.

## Mappa dei doc
`docs/ART_DIRECTION.md` · `docs/UX_PRINCIPLES.md` · `docs/GAME_DESIGN.md` · `docs/ARCHITECTURE.md` · `docs/ROADMAP.md`
Agenti: `.claude/agents/` · Skill: `.claude/skills/`
