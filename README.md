# Camera di consiglio

Una skill per Claude Code che simula la decisione di un collegio giudicante italiano su un
caso, un atto o una strategia.

Nasce come adattamento italiano delle skill "a giuria" (dodici agenti che votano colpevole o
non colpevole). In Italia la giuria non c'è: c'è un collegio che decide in camera di consiglio,
a maggioranza, e che deve motivare. La skill riproduce questo.

> È una simulazione prodotta da agenti IA. Non è un provvedimento giudiziario, non è una
> previsione dell'esito e non sostituisce la ricerca di precedenti né il lavoro dell'avvocato.

## Come funziona

1. **Fascicolo.** Raccoglie i fatti con il documento da cui ciascuno risulta ed elenca ciò che
   dagli atti non risulta. Nessun agente può presumere un fatto mancante.
2. **Questioni.** Formula le questioni da votare, nell'ordine in cui il collegio deve
   deciderle. In appello c'è una questione per ogni motivo e nessuna al di fuori dei motivi,
   salve quelle rilevabili d'ufficio.
3. **Le parti.** Un agente per parte scrive le conclusioni, indicando anche il proprio punto
   più debole; poi ciascuno replica all'argomento più forte dell'altro.
4. **Studio alla cieca.** Ogni giudice è un agente separato e studia il fascicolo senza vedere
   gli altri. Ciascuno ha un metodo di lettura diverso: dalle prove, dalle norme e dagli oneri,
   dalla tenuta della decisione in caso di impugnazione.
5. **Discussione.** Ogni giudice legge gli altri, risponde all'argomento contrario più forte e
   dichiara se mantiene o cambia posizione.
6. **Voto.** Uno alla volta, nell'ordine previsto dal codice, con il presidente per ultimo.
7. **Sentenza e verbale.** L'estensore scrive una sentenza con svolgimento, motivi e
   dispositivo; il verbale registra la posizione di ogni giudice nello studio, nella
   discussione e nel voto.

Il grado predefinito è l'appello, che è quello che una simulazione sulle carte riproduce
meglio. Varianti: primo grado collegiale, corte d'assise con i giudici popolari, cassazione, e
una versione rapida senza repliche e senza discussione.

## Cosa cambia rispetto alla giuria

| Modello "giuria" | Camera di consiglio |
|---|---|
| Dodici giurati laici | Collegio di tre giudici, o corte d'assise |
| Unanimità, altrimenti stallo | Maggioranza |
| Verdetto secco | Dispositivo e motivazione |
| Si vota insieme | Ordine di voto fisso, presidente per ultimo |

Le regole su ordine delle questioni, voto e parità sono prese dall'art. 527 del codice di
procedura penale e dall'art. 276 del codice di procedura civile, letti sul testo vigente al
15 novembre 2026. I dettagli e i limiti di questa verifica sono in
[`skills/camera-di-consiglio/references/regole.md`](skills/camera-di-consiglio/references/regole.md).

## Installazione

Copia la cartella `skills/camera-di-consiglio` tra le skill personali di Claude Code:

```bash
git clone https://github.com/avvocatopanucci/camera-di-consiglio.git
```

```bash
cp -R camera-di-consiglio/skills/camera-di-consiglio ~/.claude/skills/
```

Poi, in una nuova sessione, chiedi per esempio: "simula l'appello su questo caso".

La skill verifica le norme citate con LexItalia, uno strumento esterno che interroga
Normattiva. Senza quello strumento la simulazione funziona lo stesso, ma le norme della
sentenza restano non verificate e vanno controllate a mano.

## L'esempio

In [`esempio/email-turni`](esempio/email-turni) c'è la prima prova della skill, su un caso
**interamente inventato**: un'email aziendale rivela a 38 colleghi la chemioterapia di una
dipendente; il Tribunale accerta la violazione ma nega il risarcimento; lei appella.

- [`fascicolo.md`](esempio/email-turni/fascicolo.md) e
  [`questioni.md`](esempio/email-turni/questioni.md): il caso e le questioni da votare.
- [`parti/`](esempio/email-turni/parti): conclusioni e repliche.
- [`collegio/`](esempio/email-turni/collegio): studi, discussioni e voti dei tre giudici.
- [`VERBALE.md`](esempio/email-turni/VERBALE.md) e
  [`SENTENZA.md`](esempio/email-turni/SENTENZA.md): l'esito.
- [`collegio-v2/`](esempio/email-turni/collegio-v2): gli studi rifatti dopo la correzione
  descritta qui sotto.

### Cosa ha insegnato la prova

Nella prima prova i tre giudici, pur lavorando senza vedersi, hanno scritto la stessa
opinione: stesse soluzioni e la stessa somma. Sono lo stesso modello sullo stesso fascicolo,
quindi il 3 a 0 non valeva come conferma indipendente.

La skill è stata corretta assegnando a ogni giudice un metodo di lettura diverso e chiedendo
di scrivere, prima della propria scelta, la migliore motivazione di ogni soluzione possibile.
Rifatto lo studio sullo stesso caso, i giudici si sono divisi su tre questioni su quattro. È
una sola riprova su un solo caso: dice che i metodi producono differenze, non quanto siano
stabili. Discussione, voto e sentenza della seconda tornata non sono stati rieseguiti.

## Limiti

- Nella realtà la camera di consiglio è segreta e la sentenza non dice chi ha votato cosa. Il
  verbale dei voti è una deviazione voluta.
- Nel primo grado penale la prova si forma in dibattimento. La simulazione lavora su un
  fascicolo scritto e quella fase non la riproduce.
- I giudici sono lo stesso modello: i metodi di lettura attenuano l'uniformità, non la
  eliminano.
- Gli agenti non cercano giurisprudenza: possono citare solo i precedenti presenti nel
  fascicolo, e segnano il resto come "orientamento da verificare".
- La composizione numerica dei collegi d'appello e di cassazione è una scelta di simulazione,
  non verificata su una norma.
- Un appello con tre giudici lancia quattordici agenti: costa.

## Da dove viene l'idea

- Ahmet Bahaddin Ersoz, *12 Angry AI Agents: Evaluating Multi-Agent LLM Decision-Making Through
  Cinematic Jury Deliberation*, arXiv:2605.01986. Nel paper diciassette deliberazioni su
  diciotto finiscono senza verdetto unanime.
- I progetti che mettono un'idea "sotto processo" davanti a una giuria di agenti, tra cui
  `12-angry-ai-agents` e `court-skill`.

## Licenza

MIT. Vedi [`LICENSE`](LICENSE).
