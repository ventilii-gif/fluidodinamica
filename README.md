# 💧 Fluidodinamica in movimento

Web app interattiva in italiano per introdurre e spiegare la **fluidodinamica**
(i fluidi in moto) agli studenti del **liceo** (circa 17 anni).

Tutto è racchiuso in un **unico file** `index.html`: nessuna installazione,
nessuna dipendenza. Si apre in qualsiasi browser moderno.

## ✨ Cosa contiene

L'app è organizzata a **schede (moduli)** nella barra in alto, con tono rassicurante e motivante:

1. **Introduzione** — presentazione del percorso, come è organizzato e **riferimenti storici** (da Archimede a Reynolds)
2. **Fluidostatica** — pressione, legge di Stevino, principio di Pascal con il **torchio idraulico**, **tubo a U** con due liquidi immiscibili e principio di Archimede (3 simulazioni, 5 esercizi con formule inverse)
3. **Portata e continuità** — `Q = A·v` e l'equazione `A₁v₁ = A₂v₂`
4. **Bernoulli** — conservazione dell'energia per i fluidi
5. **Applicazioni** — effetto Venturi, teorema di Torricelli, tubo di Pitot, portanza dell'ala
6. **Viscosità e numero di Reynolds** — regime laminare e turbolento
7. **Risolutore di problemi** — strumento interattivo per verificare metodo e calcolo con i propri dati
8. **Glossario** — tutte le definizioni e le formule chiave per il ripasso

### 🗂️ Struttura di ogni modulo
Dentro ogni scheda-modulo ci sono **quattro sotto-schede** dedicate:

- 📖 **Teoria** — le idee spiegate con parole semplici
- 🎬 **Simulazioni** — animazioni interattive (Canvas) con cursori da muovere
- ✏️ **Esercizi** — un esercizio svolto **passo passo**, con **suggerimenti progressivi**
- 🎯 **Quiz** — 15 domande per modulo (**10 di teoria + 5 numeriche**), con le risposte in **posizione casuale** e feedback incoraggiante

### 🧮 Risolutore di problemi
Scheda dedicata dove lo studente sceglie il tipo di problema (continuità, Bernoulli,
Torricelli, Stevino, Archimede, galleggiamento, Reynolds), indica **cosa calcolare**,
inserisce i propri dati e ottiene **sia il metodo passo passo sia il risultato numerico**.
Può anche scrivere la propria risposta e verificare se è corretta.

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
