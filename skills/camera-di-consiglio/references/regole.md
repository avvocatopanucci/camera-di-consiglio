# Regole di deliberazione per rito e grado

Le regole su voto, maggioranza e parità qui sotto sono state lette sul testo vigente tramite
LexItalia (API Normattiva) il 15 novembre 2026. Se la skill viene usata molto tempo dopo,
rileggi gli articoli con `leggi_articolo` prima di fidarti.

La composizione numerica di corte d'appello e Cassazione (tre e cinque giudici) **non** è stata
verificata su una norma: è una scelta di simulazione. Se la riporti in un testo per terzi,
verificala prima.

## Il collegio

Collegio di tre: **Presidente**, **Consigliere A** (più anziano di servizio), **Consigliere B**
(meno anziano). Il relatore è B, salvo diversa indicazione. In primo grado chiamali "Giudice"
invece di "Consigliere".

Assise (primo grado e appello): Presidente, un giudice togato a latere, sei giudici popolari
(art. 3 l. 287/1951). Ai popolari dai età e mestiere diversi, niente altro.

Cassazione: Presidente e quattro consiglieri, uno dei quali relatore.

## Penale

Fonte: art. 527 c.p.p. (Deliberazione collegiale).

- **Ordine delle questioni.** Prima, separatamente, le questioni preliminari non ancora risolte
  e ogni altra questione relativa al processo. Se l'esito non preclude il merito: questioni di
  fatto e di diritto sull'imputazione; poi, se occorre, pene e misure di sicurezza; poi
  responsabilità civile.
- **Chi vota.** Tutti i giudici enunciano le ragioni e votano su ciascuna questione, qualunque
  sia stato il loro voto sulle altre.
- **Ordine di voto.** Il presidente raccoglie i voti cominciando dal giudice con minore
  anzianità di servizio e vota per ultimo. Collegio di tre: B, A, Presidente. In assise votano
  per primi i giudici popolari, dal meno anziano per età; poi il togato a latere; poi il
  Presidente.
- **Più di due opinioni sulla pena.** I voti per la pena più grave si riuniscono a quelli per
  la pena gradatamente inferiore, finché risulta la maggioranza.
- **Parità.** In ogni altro caso di parità prevale la soluzione più favorevole all'imputato.
  (Può capitare in assise, otto votanti.)
- **Regola di giudizio.** Condanna solo se l'imputato risulta colpevole al di là di ogni
  ragionevole dubbio (art. 533 c.p.p.). Il dubbio ragionevole va all'assoluzione, non a un
  esito intermedio.
- **Appello.** La cognizione è limitata ai punti della decisione cui si riferiscono i motivi
  (art. 597, comma 1, c.p.p.). Se appellante è il solo imputato, il collegio non può irrogare
  una pena più grave per specie o quantità, né applicare una misura di sicurezza nuova o più
  grave, né prosciogliere per una causa meno favorevole, né revocare benefici (art. 597, comma
  3). Se appellante è il pubblico ministero valgono i poteri del comma 2. Scrivi in
  `questioni.md` chi ha appellato, e togli dalle soluzioni possibili quelle vietate.
- **Sentenza.** Requisiti dell'art. 546 c.p.p.: intestazione, parti, imputazione, conclusioni
  delle parti, concisa esposizione dei motivi di fatto e di diritto con i risultati acquisiti,
  i criteri di valutazione della prova e le ragioni per cui le prove contrarie non sono
  ritenute attendibili, dispositivo con gli articoli di legge applicati.

## Civile

Fonte: art. 276 c.p.c. (Deliberazione).

- **Ordine delle questioni.** Gradatamente: prima le questioni pregiudiziali proposte dalle
  parti o rilevabili d'ufficio, poi il merito.
- **Maggioranza e ordine di voto.** Si decide a maggioranza. Vota per primo il relatore, poi
  l'altro giudice, infine il presidente.
- **Più soluzioni senza maggioranza.** Il presidente mette ai voti due soluzioni per escluderne
  una; poi la non esclusa contro la restante; e così via finché ne restano due, su cui si vota
  in via definitiva.
- **Motivazione.** La stende il relatore, salvo che il presidente la stenda lui stesso o la
  affidi all'altro giudice.
- **Regola di giudizio.** Onere della prova su chi afferma il fatto; per il nesso causale il
  criterio del "più probabile che non". Quest'ultimo è un criterio giurisprudenziale: nella
  sentenza va indicato come tale, senza estremi di precedenti che non siano nel fascicolo.
- **Appello.** Una questione per ciascun motivo; ciò che non è stato impugnato non si ridiscute.
  Le regole sull'ammissibilità dell'appello e sui nuovi mezzi di prova non sono riportate qui:
  se una questione dipende da esse, leggi la norma con LexItalia prima di formularla.

## Cassazione

Solo questioni di legittimità: il collegio non rivaluta i fatti accertati dal giudice di
merito. Ogni questione corrisponde a un motivo di ricorso. I motivi di ricorso ammessi (penale
e civile) non sono riportati qui: leggi la norma con LexItalia quando imposti `questioni.md`, e
metti l'ammissibilità di ciascun motivo tra le questioni preliminari. L'esito possibile è
rigetto, inammissibilità, annullamento o cassazione con o senza rinvio.

## Primo grado

Stesse regole di voto. Nel fascicolo va scritto in evidenza che la prova non è stata formata
in contraddittorio davanti al collegio: i giudici valutano solo documenti e verbali presenti,
e una dichiarazione riferita ma non documentata non è prova.
