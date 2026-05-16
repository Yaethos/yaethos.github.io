---
title: Guida Foglio Pre-Iscrizioni
categories: [Misc]
date: 2026-05-16
tags: []     # TAG names should always be lowercase
---
# Introduzione
Buonasera e benvenuti alla guida su come utilizzare al meglio il foglio Pre-Iscrizioni. Per quanto possa sembrare complicato in realtà è attualmente semplice da usare, con un controllo principale svolto da me e delle sezioni dedicate per gli insegnanti che possono essere gestite liberamente. 

Prima di continuare è utile una distinzione di terminologia: con il termine *Pre-Iscritto* intendiamo una persona che ha compilato il form. Con una persona in *Waiting List* intendiamo qualcuno che ha compilato il form, ha ricevuto le informazioni necessarie dalla segreteria, è pronto/a ad iscriversi ma non può attualmente farlo per motivi esterni al suo controllo (es. lab pieni, quadrimestre in corso o finito...). 

Questa distinzione è cruciale per evitare che la Waiting List venga riempita da persone che non rispondono o spariscono. La Waiting List vuole quindi essere una lista di persone già informate che aspettano solo che si liberi un posto.

# Struttura File
Il file si divide in tre sezioni principali.
![Desktop View](/assets/img/preiscr/Sezioni.png)
<br>
La prima sezione (in rosso) contiene il foglio risposte, in cui arrivano le compilazioni per intero. Aprendo questo foglio di lavoro si noteranno due tabelle affiancate, una viola e una verde.
![Desktop View](/assets/img/preiscr/Raw_1.png)
<br>
![Desktop View](/assets/img/preiscr/Raw_2.png)
<br>

La sezione viola, anch'essa composta da un foglio solo, contiene la Waiting List.
La sezione azzurra contiene un foglio per ogni insegnante e, infine, la sezione verde contiene i fogli che vengono utilizzati per calcolare metriche e statistiche.

## Prima Sezione (foglio risposte)
La tabella viola è la tabella a cui vengono aggiunte le risposte dei questionari, e possiamo infatti vedere tutti i campi presenti anche nel form di preiscrizione. La tabella verde invece è una prima rielaborazione dei dati. In questa tabella vengono (i) tolti alcuni dati di bassa rilevanza e (ii) iniziano a venire aggiunte informazioni di interesse gestionale.
Ad oggi, le informazioni che vengono aggiunte sono:
- Una colonna *Stato*. I possibili stati sono molteplici e si riferiscono allo stato della persona. Alcuni esempi sono:
    - "_Da Sentire_": significa che la pre-iscrizione deve ancora essere _verificata_ dalla segreteria
    - "_Iscritto_": significa che la persona risulta già partecipante ad un lab.
    - "_Iscritto e in WL per altro_": significa che la persona risulta iscritta ad un lab ma è interessata ad un altro
    - "_Rifiutato_": significa che la persona ha rifiutato per più volte proposte (o non ha risposto). Una persona con questo stato non viene più contattata.
    - "_Smistato_": significa che la persona è stata inviata ad uno degli insegnanti con l'obiettivo di finalizzare l'iscrizione
    - "In WL": significa che la persona è volenterosa di iscriversi ma non può farlo per motivi esterni
- Una colonna *WL*. Questa colonna contiene i laboratori per cui la persona è in Waiting List. Questo vuol dire che, in realtà, esiste una sotto-Waiting List per ogni laboratorio, e lo vedremo in seguito.
- Una colonna *Contatto di Riferimento*. Questa colonna contiene il nome degli insegnanti a cui è stato affidato il pre-iscritto. La selezione dell'insegnante è influenzata principalmente dal lab di interesse del preiscritto.
- Una serie di colonne, una per ogni quadrimestre/lab spot. Queste colonne servono per tenere traccia dello storico delle risposte di ogni pre-iscritto. Attraverso queste colonne è possibile ricordare a quali lab spot qualcuno ha partecipato, e come ha risposto ai tentativi di contatto.

*IMPORTANTE:* Ad oggi, l'unico ruolo che può modificare queste colonne è la segreteria. Agli insegnanti non è richiesta la modifica dirette di queste colonne, in quanto utilizzano codici e nomenclature specifiche utili ad un coordinamento generale, piuttosto che ad un controllo granulare che invece è più utile all'insegnante. La colonna "Contatto di Riferimento Selezionato" e "WL" possono essere modificate con cognizione di causa (spiegato più avanti).

## Seconda Sezione (Waiting List)
La seconda sezione, a prima vista, differisce poco dalla colonna viola del foglio risposte. Questo perché, per accedere alla vista della Waiting List effettiva, dobbiamo utilizzare una *Vista Filtro*. Per attivare una vista filtro, bisogna cliccare il simbolo affianco al nome della tabella:
![Desktop View](/assets/img/preiscr/WL_Filtro1.png)
<br>
Questo farà comparire un menù a tendina, da cui è possibile selezionare una tra più opzioni.
![Desktop View](/assets/img/preiscr/WL_Filtro2.png)
<br>

Attualmente è presente una *Vista Filtro* per ogni percorso (Voce, Misto, Percu, Direzione, Mel-Arm). È presente inoltre una vista di tutta la Waiting List (WL Intera). Ricordo che la Waiting List differisce dal foglio risposte per il fatto che solo qualcuno che si è dimostrato veramente interessato viene inserito in Waiting List.

Se volete aggiungere pre-iscritti alla Waiting List del vostro Lab basta aggiungere il nome del lab *nel foglio risposte, tabella verde, colonna "WL"*. Se provate ad aggiungerlo nel foglio della WL vi darà un errore.

*IMPORTANTE:* a parte quest'ultimo punto, la modifica da parte degli insegnanti è sconsigliata a meno che non si sappia cosa si sta facendo (e soprattutto perchè).

## Terza Sezione (Insegnanti)
Anche in questo caso, a prima vista queste sezioni sono quasi del tutto simili al foglio risposte. Questo perchè, ancora una volta, è necessario attivare la *Vista Filtro*. Ogni sezione insegnante ha attualmente una Vista Filtro sola, e attivarla ci porta ad avere la lista di persone che hanno l'insegnante che dà il nome alla sezione come Contatto di Riferimento.

È bene tenere a mente che queste sezioni sono collegate unidirezionalmente con il foglio risposte. Qualsiasi modifica nel foglio rispsote sarà rispecchiata in questi fogli (se ad esempio nel foglio risposte viene aggiunto cambiato il contatto di riferimento di un pre-iscritto, questo verrà cambiato anche in tutti i fogli specifici degli insegnanti). Tuttavia, qualsiasi cambiamento effettuato dentro il foglio insegnanti non verrà riportato nel foglio risposte. 
Inoltre, una volta che una cella viene modificata, viene disconnessa dal foglio risposte e non verrà più aggiornata con esso. Ci sono pochi casi in cui serve sapere ciò, quindi intanto lo dico poi se ci dovessero essere problemi potete scrivermi direttamente.

Se volete aggiungere pre-iscritti alla vostra Vista Filtro basta aggiungere il vostro nome tra i contatti di riferimento *nel foglio risposte, tabella verde, colonna "Contatti di Riferimento Selezionati"*. Se provate ad aggiungerlo nel vostro foglio vi darà un errore.

I fogli insegnanti hanno anche la stessa sfilza di colonne "storico" che ci sono nel foglio risposte. In passato si aveva una lista di simboli e codici per indicare diversi tipi di risposta del pre-iscritto, ma ora con i fogli dedicati potete gestirvela un po' come volete. Sarà compito mio riportare lo storico sul foglio risposte, in modo che ci sia una versione ufficiale e completa. Per questo vi chiedo di fare in modo di avere un sistema quantomeno consistente.

## Varie ed eventuali
La *Vista Filtro* deve essere reinserita ogni volta che si apre il foglio, ed è possibile che ogni tanto sia necessario aggiornare la pagina affinché modifiche recenti siano registrate dal vostro browser.

Sto anche combattendo con qualcosa che non capisco bene se sia un bug o un errore mio, per il quale le nuove pre-iscrizioni non compaiono nei fogli dedicati e nel foglio WL. Se questo dovesse succedere fatemi sapere.

Ben poco di quanto descritto finora è la versione migliore possibile del file. Se avete proposte, o se trovate qualcosa particolarmente macchinoso, sentitevi liberi di scrivermi anche solo per dirmi che vi trovate male con qualcosa. Se riuscite anche a dirmi come vorreste che funzionasse (senza scendere in dettagli tecnici, solo l'idea va benissimo) sarebbe utile.

# Workflow previsto
La segreteria riceve la pre-iscrizione nuova e contatta al più presto la persona che ha compilato. In questo primo scambio fornisce informazioni in merito ai costi, alle date e al programma, oltre che rispondere ad eventuali domande. Se la persona conferma l'interesse a partecipare, la segreteria inserisce quella persona nella Waiting List del Lab in questione.

Gli insegnanti controllano la Waiting List dei propri laboratori e contattano le persone lì presenti per formare i gruppi dei lab. Questo controllo deve essere fatto abbastanza regolarmente nei periodi di preparazione di un nuovo quadrimestre.

Ogni insegnante è chiaramente libero di contattare persone che non hanno mostrato interesse per il proprio Lab. Per tenere traccia delle risposte chiederei, in questo caso, di aggiungersi come contatto di riferimento nel foglio risposte. Questo fa sì che quel pre-iscritto compaia anche nel foglio personale, dando così la possibilità di segnare il tipo di risposta ricevuta.

È possibile che la segreteria non sia sicura se posizionare qualcuno nel grado 1 o 2  (o 3) di un lab. In questo caso, il dubbio sarà esplicitato tramite un commento presente nel foglio personale dell'insegnante coinvolto, rimettendo a lui la scelta. La scelta dovrà essere inserita nel foglio risposte, in corrispondenza della voce "WL".
