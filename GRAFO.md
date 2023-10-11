Il compito di questo file e cercare di descrivere e definire cosa è un grafo e principalmente cosa è un nodo.

Un nodo è la rappresentazione fisica di un oggetto (blocco) astratto, il nodo più semplice che si può immaginare è definito da una forma (struttura), da un contenuto, dai riferimenti.

Una struttura di un nodo categorizza la tipologia di nodo che a seconda della topologia può presentare diverse proprietà/collegamenti e visualizzazione:
    Ad esempio una definizione assiomatica viene richiamata ma non si collega / non ha implicazioni.
    Un lemma essendo un'affermazione precedente a un teorema deve permettere il collegamento diretto a un teorema
    Un'osservazione è figlia / diretta conseguenza di una frase o affermazione.
    E altre strutture.
    ?Proporrei: la struttura permette di leggere dei codici nel contenuto ed essere interpretati a seconda della struttura?

Un grafo essendo comunque basato su nodi che sono a loro volta astratti deve essere astratto. Il grafo è un sistema di interconessione di nodi. Deve essere dinamico a seconda delle necessità, concettualmente deve prendere e collegare i nodi astratti globali (appartenenti al cloud) e generare quindi un grafo relativo.
I collegamenti sono generati a seconda della necessità: file: io persona sto scrivendo una tesi/ dispensa e a seconda dei nodi che uso e come li scrivo viene generato un grafo che raggruppa questi nodi.
Esempio

\nodeServer{disBernoulli#213#}

...
\subsection{Sviluppi}
    \begin{prop}[Sviluppo di un binomio, non so che mette in realtà]
        Vale $1=0$
    \end{prop}
    \begin{dimostrazione}
        $a=43$ Prova kdsjsdidsad

        Ciao usando \refServer{#213#} concludiamo $1=0$
    \end{dimostrazione}
...

Crea nel cloud il nodo prop[Sviluppo...]
Prende dal cloud il nodo #213# e il nodo appena creato, il nodo creato appartiene alla sottosezione sviluppi quindi sarà in una certa maniera raggruppato in questa sottosezione in maniera insiemistica.

Nota: globalmente un nodo non appartiene a nessuna sottosezione o sezione, presenta giusto degli hashtag per utilità di ricerca.
In fase di loading da globale->locale un nodo acquisisce certe proprietà determinate dal file, utili alla lettura/visione del file. Mi sto immaginando che un file può essere interpretato "visualizzato" in diverse maniere: pdf, grafo, "pagina html".


Altro grosso problema che penso sia da gestire, date le definizioni A,B,C,D globali che richiamo localmente devo poterle usare nel mio file
ma usando la MIA notazione. Ad esempio un generico prodotto scalare viene denotato con < , > e un prodotto hermitiano con h( , ) ma i fisici
rappresentano il prodotto hermitiano come < | >. Vorrei che ogni parola del testo che possa essere riferita alla sua definizione permetta un link a cosa si riferisce. Ad esempio:
Se scrivo sia V spazio vettoriale, e v un vettore appartenente a V ($v\in V$ equivalentemente) allora b(v,v)>=0.
Vorrei che al click di un tasto il mouse passa a una modalità che permette di aprire le referenze anche sulle parole / richiami del tipo
spazio vettoriale, v vettore, b( , ) forma bilineare simmetrica. E queste notazioni devono cambiare nel file, ho una mezza idea di come gestirla ma dovremmo confrontarci e discuterne.

Un'idea di soluzine, un nodo generico verrà chiamato struct.
Partiamo dall'ente "primitivo" gli oggetti di lavoro: ovvero definizioni e assiomi, darei per buono gli assiomi che sono abbastanza banali sono semplicemente delle proprietà perciò inizierei a lavorare sulle definizioni.

Prima regola, una definizione può essere richiamata solo dopo essere stata scritta / definita (se non nel file almeno deve esistere una refenza di parola precedente).
Nel file devono essere presenti le reference di parola, ad esempio se in un teorema ci sta scritto spazio vettoriale allora deve essere possibile linkare la parola: spazio vettoriale con la sua adeguata definizione che può avere più tipi di notazione.
Nel mio file posso scrivere la mia bellissima definizione:
definzione: {parola}
(oppure una reference di parola)
ref: {parola->definizione{parola}} //Se voglio esplicitamente chiederlo io, altrimenti potrei usare / impostare degli abreviativi:
ref: {spv->definizione{spazio vettoriale}}
theo: {... Sia A parola}

La lettera A è un pattern UNICO dentro l'ambiente theo che permette di collegare l'oggetto astratto A con la definizione. (Magari potremmo trovare un modo per poter aggiungere delle ipotesi su A così che siano sempre visualizzabili)

Le notazioni sono un po' più complicate, ovviamente data una definizione ho un UNICO oggetto astratto che la rappresenta ad esempio: PRODOTTO SCALARE B( , ), dove B( , ) è un pattern. Questo pattern a seconda della notazione che si imposta mi dice di visualizzare B( , ) come < , > oppure come < | > nel mio file. Abbiamo detto che le struct devono essere oggetti (in particolare sono statici) quindi le definizioni devono avere la proprietà notazione: definizione{parola}->not= notazioneA.
L'impostazione di notazione deve essere coerente quindi notazioneA deve specificare quale pattern vuole (che deve essere lo stesso della definizione) e come lo visualizza. Di base ogni definizione deve avere una notazione sua.

L'utilità di ref: .... è che per richiamare la definizione spazio vettoriale è sufficiente che scriva: "spazio vettoriale" o se lo imposto un suo abreviativo, a maggior ragione se trovo il pattern Sia A spazio vettoriale allora mi associa ad A la notazione scelta. Ci sono dei problemi con questo se nello stesso contesto usassi due spazi vettoriali? allora visualizzerei la stessa notazione per due oggetti che sono la stessa cosa ma sono distinti. Dovremmo fare che se in un contesto ci sono più richiami della stessa definizione con pattern diversi: Siano A,B spazi vettoriali allora la notazione deve gestire visualizzazioni diverse per A e per B.
Noi umani scriveremmo due lettere diverse oppure associeremmo un numero ad esempio A_1, A_2 beh notazione dovrebbe poter gestire queste cose o averle nella configurazione.

Concettualmente tutto è un oggetto come gli oggetti di programmazione, le struct dentro un file oltre che essere possibilmente visualizzabili hanno delle proprietà e dei metodi interni. Ad esempio voglio trattare una tematica che usa definizioni e terminologie che non voglio siano presenti esplicitamente nel file, allora richiamo tutte le struct di cui ho bisogno e le imposto a seconda della mia utilità. Di base se importo la definizione di spazio vettoriale allora nel file ogni volta che compare il pattern Sia A spazio vettoriale deve essere possibile unire la parola spazio vettoriale con la definizione e dentro il contesto il pattern A rappresenta uno spazio vettoriale quindi anch'esso si ricollega alla definizione.
