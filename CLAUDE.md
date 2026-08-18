# CLAUDE.md — Fluidodinamica in movimento

Guida per assistenti AI che lavorano su questo repository. Leggila prima di
modificare il codice.

## Cos'è

Web app didattica **in italiano** che introduce la **fluidodinamica** a
studenti di **liceo** (~17 anni). Tutto in un **unico file** `index.html`
(~2800 righe): **nessuna installazione, nessuna dipendenza, nessun build**.
Si apre facendo doppio clic sul file in un browser moderno.

Il pubblico è composto da studenti: il tono deve restare **rassicurante,
incoraggiante e semplice**, e tutti i contenuti devono essere **in italiano**.

## File nel repository

- `index.html` — l'intera applicazione (HTML + CSS + JS in-line).
- `README.md` — descrizione del progetto per utenti finali.
- `.nojekyll` — dice a GitHub Pages di servire i file così come sono.

## Come eseguire e testare

Non esiste una suite di test automatica. Il testing è **manuale nel browser**:

```bash
# Opzione 1: apri direttamente il file
xdg-open index.html      # (o doppio clic dal file manager)

# Opzione 2: server statico locale
python3 -m http.server 8000   # poi apri http://localhost:8000
```

Dopo ogni modifica, verifica a mano:
- la navigazione tra le **schede** (moduli) e le 4 **sotto-schede**;
- che le **animazioni Canvas** partano e si fermano cambiando scheda;
- i **cursori** (slider) delle simulazioni;
- gli **esercizi** passo passo e la verifica della risposta;
- i **quiz** di modulo e il **quiz finale** (punteggio, ripasso errori);
- il **tema chiaro/scuro** e la **barra di progresso**;
- il layout **responsive** (ridimensiona la finestra).

## Deploy

Pubblicato tramite **GitHub Pages dalla radice** del repository (branch →
`/ (root)`). Il file `.nojekyll` deve restare presente. Nessun passo di build.

## Architettura

Tutto il JavaScript è in un unico `<script>` (da riga ~330). L'app è
**data-driven**: la struttura dei contenuti vive in un'unica costante e il
DOM viene **generato**, non scritto a mano.

### Sorgente unica dei contenuti: `SECTIONS`

`const SECTIONS = [...]` (index.html:1089) è la **fonte di verità** di tutti
i moduli. Ogni oggetto sezione descrive teoria, simulazioni, esercizi e quiz.
**Per aggiungere o modificare contenuti, modifica `SECTIONS`** — non scrivere
markup di sezione a mano.

Funzioni che costruiscono la UI a partire da `SECTIONS`:

| Funzione | Riga | Ruolo |
|---|---|---|
| `buildNav()` | :2084 | Costruisce la barra di navigazione dei moduli |
| `buildSection(s, i)` | :2328 | Renderizza un modulo e le sue 4 sotto-schede |
| `renderQuiz(...)` | :2501 | Genera il quiz di un modulo (risposte mescolate) |
| `buildFinalQuiz()` | :2602 | Quiz finale riepilogativo (20 quesiti) |
| `buildSolver()` | :2246 | Il "Risolutore di problemi" interattivo |

Ogni modulo ha 4 sotto-schede: **Teoria · Simulazioni · Esercizi · Quiz**.

### Animazioni (Canvas)

Le simulazioni usano `<canvas>`, non SVG:
- `setupCanvas(...)` (:368) prepara il canvas (DPI, dimensioni).
- Ogni simulazione ha un proprio `frame()` in loop con
  `requestAnimationFrame`.
- `readPalette()` (:337) legge le **variabili CSS** (`--water`, `--particle`,
  …) così i colori del canvas seguono il tema chiaro/scuro.
- `startAnims()` (:2710) e `stopRunningAnims()` (:2716) avviano/fermano i
  loop quando si cambia scheda — importante per non lasciare animazioni
  attive in background.

### Tema chiaro/scuro

- Palette definita con **CSS custom properties** su `:root` e
  `[data-theme="dark"]` (in cima al `<style>`).
- `applyTheme(theme)` (:2751) imposta l'attributo `data-theme` e persiste la
  scelta in `localStorage['fluidodinamica_theme']`.
- Il codice del canvas **non** deve usare colori hardcoded: passa sempre da
  `readPalette()` per restare coerente con il tema.

### Progresso e stato

- `const STORE_KEY = 'fluidodinamica_progress_v1'` (:2069); `saveProgress()`
  (:2072) salva le sezioni completate in `localStorage`.
- `shuffle(arr)` (:351) mescola le risposte dei quiz.
- `goTo(i)` (:2727) naviga tra le sezioni; `updateGlobal()` aggiorna la barra
  di progresso.

## Convenzioni

- **Lingua**: italiano ovunque — testo UI, molti commenti e stringhe. I nuovi
  contenuti devono essere in italiano e mantenere il tono didattico.
- **Zero dipendenze**: niente npm, bundler, framework o CDN. Non introdurre un
  passo di build né dipendenze esterne senza che sia richiesto esplicitamente.
- **Un solo file**: HTML, CSS e JS restano dentro `index.html`.
- **Matematica/fisica**: usa i caratteri Unicode (ρ, Δ, ₁, ₂, ·) e le classi
  `.mono`/formula già presenti; mantieni la coerenza con lo stile esistente.
- **Canvas segue il tema**: colori sempre da variabili CSS via `readPalette()`.
- **Privacy**: l'app non invia nulla in rete; l'unico stato è in
  `localStorage`. Non aggiungere chiamate di rete o tracciamento.

## Note per le modifiche

- Il file è grande: usa la ricerca per raggiungere `SECTIONS` (:1089) o la
  funzione di rendering pertinente prima di modificare.
- Aggiungere un modulo = aggiungere un oggetto a `SECTIONS`; le funzioni di
  build lo raccolgono automaticamente. Verifica poi nav, sotto-schede, quiz e
  progresso nel browser.
- Prima di aggiungere una nuova simulazione, riusa `setupCanvas` e il pattern
  `frame()`/`readPalette()` già presenti invece di introdurne uno nuovo.
