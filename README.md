# 💧 Fluidodinamica in movimento

Web app interattiva in italiano per introdurre e spiegare la **fluidodinamica**
(i fluidi in moto) agli studenti del **liceo** (circa 17 anni).

Tutto è racchiuso in un **unico file** `index.html`: nessuna installazione,
nessuna dipendenza. Si apre in qualsiasi browser moderno.

## ✨ Cosa contiene

Un percorso guidato in 5 tappe, con tono rassicurante e motivante:

1. **Introduzione** — che cos'è un fluido, il fluido ideale, le linee di corrente
2. **Portata e continuità** — `Q = A·v` e l'equazione `A₁v₁ = A₂v₂`
3. **Equazione di Bernoulli** — conservazione dell'energia per i fluidi
4. **Applicazioni** — effetto Venturi, teorema di Torricelli, tubo di Pitot, portanza dell'ala
5. **Viscosità e numero di Reynolds** — regime laminare e turbolento

Per ogni sezione trovi:

- 📖 **Teoria** spiegata con parole semplici
- 🎬 **Animazioni interattive** (Canvas) con cursori da muovere
- 🔢 **Esempi numerici** con soluzione passo passo
- 🎯 **Quiz** con le risposte in **posizione casuale** e feedback incoraggiante

Altre caratteristiche:

- 🌙 **Tema chiaro (giorno) e scuro (notte)**, con pulsante in alto a destra
- 📈 **Barra di progresso**: le sezioni completate vengono salvate sul dispositivo
- 📱 Layout **responsive** per computer, tablet e smartphone

## ▶️ Come provarla in locale

Scarica il progetto e fai **doppio clic su `index.html`**: si apre nel browser. Tutto qui.

## 🌐 Pubblicazione su GitHub Pages (gratis)

1. Vai su **Settings** del repository → sezione **Pages**.
2. Alla voce *Build and deployment* → *Source*, scegli **Deploy from a branch**.
3. Seleziona il branch da pubblicare (es. `main`) e la cartella **`/ (root)`**, poi **Save**.
4. Dopo qualche minuto l'app sarà online all'indirizzo:
   `https://<tuo-utente>.github.io/fluidodinamica/`

> Poiché il sito è un semplice `index.html` nella radice, GitHub Pages lo mostra
> automaticamente senza altra configurazione.

## 🔒 Privacy

L'app **non** raccoglie dati e **non** invia nulla in rete: il progresso dei quiz
è salvato solo nel browser (localStorage) del singolo dispositivo.

---

Realizzato come strumento didattico. Buono studio! 🚀
