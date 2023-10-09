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
