---
name: camera-di-consiglio
description: Simula la decisione di un collegio giudicante italiano su un caso, un atto o una strategia. Le parti scrivono conclusioni e repliche, tre giudici (o la corte d'assise con i giudici popolari) studiano il fascicolo ciascuno per conto proprio, discutono, votano questione per questione nell'ordine previsto dal codice e l'estensore scrive una sentenza motivata, con il verbale dei voti. È l'adattamento italiano delle skill "giuria di 12 agenti". Usala quando l'utente chiede "camera di consiglio", "metti sotto processo", "simula il collegio", "simula l'appello", "come deciderebbe un collegio", "stress test dell'atto davanti a un collegio", per lavoro, per un corso o per la newsletter. Non è una previsione dell'esito e non sostituisce la ricerca di precedenti.
---

# Camera di consiglio

Simula un collegio italiano che decide a maggioranza e motiva. Non c'è giuria, non c'è unanimità,
non c'è verdetto secco: l'esito è una sentenza con motivi e dispositivo, più un verbale dei voti.

Tutto quello che produci va in una cartella nuova nella directory di lavoro:
`.camera-di-consiglio/<AAAA-MM-GG>-<nome-breve>/`. Non modificare mai i file del fascicolo.

Prima di cominciare leggi `references/regole.md` (ordine di voto, parità, regola di giudizio per
rito e grado) e `references/ruoli.md` (le istruzioni da dare a ciascun agente).

## Cosa chiedere, e cosa no

Servono tre cose. Ricavale dal messaggio e dai file; chiedi solo quelle che mancano davvero.

1. **Il materiale**: atti, sentenza impugnata, documenti, oppure la descrizione del caso.
2. **Il rito**: penale o civile. Se il materiale lo rende ovvio, non chiederlo.
3. **Il grado**: se non è indicato usa l'**appello**, che è il grado che la simulazione
   riproduce meglio (si decide sulle carte, entro i motivi). Se manca una sentenza da impugnare,
   usa il primo grado collegiale e dichiara nel fascicolo che la fase di formazione della prova
   non è simulata.

Varianti: `appello` (predefinita), `primo-grado`, `assise`, `cassazione`, e `rapida` (senza
repliche e senza discussione: più veloce, meno attendibile sul cambio di opinione).

## Le regole che non si derogano

- **Niente vuoti colmati.** Il fascicolo contiene solo ciò che risulta dalle fonti. Un atto, una
  data, una prova o un'udienza che non risulta si scrive come mancante. Nessun agente può
  supporre un fatto che non è nel fascicolo: può solo dire che manca e trarne le conseguenze
  sull'onere della prova.
- **Nessuna posizione assegnata ai giudici.** Non dire a un giudice come orientarsi, né quale
  esito ti aspetti. I giudici non hanno personaggi né pregiudizi; solo i giudici popolari
  dell'assise hanno un profilo (età, mestiere), mai un'opinione di partenza.
- **Un metodo diverso per ciascun giudice.** I giudici sono lo stesso modello sullo stesso
  fascicolo: senza differenze di metodo scrivono tre volte la stessa opinione. A ciascuno va
  assegnato un metodo di lettura tra quelli di `references/ruoli.md` (dalle prove, dalle norme,
  dalla tenuta della decisione). Il metodo dice da dove partire, non dove arrivare.
- **I giudici sono agenti separati.** Ogni giudice è un subagente distinto, in ogni fase. Non
  scrivere tu i voti e non far scrivere più giudici allo stesso agente.
- **Niente giurisprudenza a memoria.** Parti e giudici citano solo i precedenti presenti nel
  fascicolo. Un orientamento che ricordano ma non è nel fascicolo si scrive come
  "orientamento da verificare", senza estremi.
- **Le norme si verificano.** Prima di consegnare, ogni norma citata nella sentenza va
  verificata con LexItalia (`risolvi_norma`, o `leggi_articolo` se ne riporti il contenuto), e
  il link va riportato come arriva.

## Procedura

### 1. Fascicolo
Leggi il materiale e scrivi `fascicolo.md`: parti, fatti con la fonte di ciascuno (documento e
pagina), atti disponibili, provvedimento impugnato se c'è, domande o imputazione, e un elenco
"Non risulta dagli atti". Sul rito, sul grado e sulle lacune che cambiano l'esito fermati e
chiedi; sul resto procedi.

### 2. Questioni
Scrivi `questioni.md`: l'elenco numerato delle questioni che il collegio voterà, ciascuna
formulata come domanda con le soluzioni possibili. Ordine: prima le preliminari o
pregiudiziali, poi il merito (fatto, diritto), poi pena o quantum, poi spese. In appello c'è
almeno una questione per ogni motivo, e nessuna questione fuori dai motivi. In cassazione solo
questioni di legittimità. Vedi `references/regole.md`.

### 3. Le parti
Lancia in parallelo un agente per parte (istruzioni in `references/ruoli.md`). Ciascuno riceve
fascicolo e questioni e scrive le proprie conclusioni: `parti/<parte>-conclusioni.md`. Poi, in
parallelo, un secondo giro in cui ciascuno legge le conclusioni dell'altro e replica:
`parti/<parte>-replica.md`. Con `rapida` salta le repliche.

### 4. Studio del fascicolo (alla cieca)
Lancia in parallelo un agente per ogni giudice. Ciascuno riceve fascicolo, questioni e scritti
delle parti, il proprio metodo di lettura, e **non** vede gli altri giudici. Scrive
`collegio/<giudice>-studio.md`: per ogni questione prima la migliore motivazione di ciascuna
soluzione possibile, poi quella verso cui propende, le ragioni, e il punto su cui è meno
sicuro. Dove si vota una somma o una misura, indica prima il minimo e il massimo che ritiene
difendibili, poi la cifra. Il relatore scrive in più la relazione (fatti e questioni, senza
opinione).

Quando gli studi sono pronti, confrontali. Se coincidono in tutto (stesse soluzioni, stesse
cifre, stessi argomenti), non rilanciarli per ottenere dissenso: annotalo nel verbale e dillo
nella consegna, perché in quel caso l'unanimità vale come una sola opinione.

### 5. Discussione
Lancia in parallelo un agente per ogni giudice. Ciascuno riceve il proprio studio e quelli
degli altri e scrive `collegio/<giudice>-discussione.md`: per ogni questione l'argomento
contrario più forte tra quelli letti, la risposta a quell'argomento, e se mantiene o cambia la
propria posizione, con il motivo. Con `rapida` salta questa fase.

### 6. Voto
Qui i giudici votano **uno alla volta**, nell'ordine di `references/regole.md`, e ciascuno vede
i voti di chi ha votato prima. Il presidente vota sempre per ultimo.

- Se ci sono questioni preliminari, votale per prime e conta. Se l'esito preclude il merito,
  la votazione finisce lì.
- Poi il merito. Ogni giudice vota su ogni questione, anche se è rimasto in minoranza su una
  precedente: in quel caso decide la questione successiva dando per acquisita la soluzione
  della maggioranza.
- Ogni voto è una soluzione tra quelle di `questioni.md` più tre righe di ragioni.

Conta i voti tu, con le regole su maggioranza e parità di `references/regole.md`, e scrivi
`VERBALE.md`: tabella questione per giudice, esito di ogni questione, e per ciascun giudice
dove ha cambiato posizione tra studio, discussione e voto.

### 7. Sentenza
Lancia l'agente estensore: è il relatore se ha votato con la maggioranza sulle questioni
decisive, altrimenti un altro giudice della maggioranza. Riceve fascicolo, scritti delle parti,
verbale e gli scritti dei giudici della maggioranza. Scrive `SENTENZA.md` secondo lo schema di
`references/ruoli.md`. La motivazione deve rispondere a ogni argomento della parte soccombente
e non può contenere fatti assenti dal fascicolo.

### 8. Controllo e consegna
- Rileggi la sentenza contro il fascicolo: ogni fatto ha la sua fonte, il dispositivo coincide
  con il verbale, nessun precedente con estremi fuori dal fascicolo.
- Verifica le norme con LexItalia e aggiungi in fondo alla sentenza la nota sulle fonti.
- In testa a `SENTENZA.md` e `VERBALE.md` metti l'avvertenza: "Simulazione prodotta da agenti
  IA. Non è un provvedimento giudiziario né una previsione dell'esito."

Nella risposta all'utente riporta: il dispositivo in una frase, il conteggio dei voti sulle
questioni decisive, i due o tre argomenti che hanno deciso, quelli della parte soccombente che
il collegio ha faticato a superare, chi ha cambiato idea e perché, e che cosa mancava nel
fascicolo. Collega i file. Di' sempre che cosa la simulazione non ha fatto (prova non formata
in contraddittorio, precedenti non cercati).

## Limiti da dichiarare

- Nella realtà la camera di consiglio è segreta e la sentenza non dice chi ha votato cosa. Il
  verbale dei voti è una deviazione voluta: serve a vedere dove la tesi cede.
- Gli agenti tendono ad ancorarsi alla prima posizione. Per questo lo studio è alla cieca e
  nessuna posizione è assegnata; un collegio che non cambia mai idea non prova che la tesi sia
  solida.
- I giudici sono lo stesso modello: tendono anche a pensarla allo stesso modo fin dall'inizio.
  I metodi di lettura attenuano il problema, non lo eliminano. Un 3 a 0 dice che il fascicolo
  porta lì un lettore attento, non che tre giudici diversi sarebbero d'accordo.
- Il collegio decide solo su ciò che gli hai dato: un fascicolo incompleto produce una sentenza
  sicura di sé su basi incomplete.
