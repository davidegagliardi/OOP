# Programmazione a oggetti
Appunti a cura di *Andrea Abriani (@aabriani), Davide Gagliardi (@davidegagliardi), Andrea Braghiroli*

### Fattori qualità software:

#### Esterni

* **Estendibilità**: sistema amplia funzionalità che il software aveva in precedenza. Programmazione ad oggetti viene resa più semplice.
* **Riusabilità**: software e componenti possono essere riutilizzati per un insieme di requisiti che possono essere diversi da quelli precedenti.



#### Interni:
*fattori percepibili al codice della sorgente*

*	**Strutturazione**: codice viene scritto in modo tale da astrarre delle singole parti. E’ possibile un’individuazione di parti di software indipendenti dalle altre (es. Input/output può essere posizionato in zona differente).
*	**Modularità**: collegata alla strutturazione. Va oltre la struttura e indica che può essere usata in modo diverso e con componenti può raggiungere scopi e requisiti differenti. (Il codice può essere utilizzato  per scopi diversi).
*	**Comprensibilità**: software strutturato in modo che corrisponda alla descrizione del dominio.

### Caratteristiche programmazione a oggetti

*Key idea: connessione esplicita funzioni-dati (non vi sono più struct con metodi e costruttori)*

In precedenza, vi era una procedura che lavorava su variabili globali. Ora invece, le funzioni sono connesse ai dati. Questo delimita ciò che le funzioni possono fare. Questo avviene tramite la procedura di **incapsulamento**. Questa procedura non avviene per la sicurezza dei dati bensì per la visibilità. Solo alcuni metodi e funzioni potranno accedere agli elementi di una determinata classe.

#### Classe
Le classi sono legate in gerachie. Una eredita l'altra per creare una struttura.

Si pone enfasi sulla rappresentazione. In caso di errori si andrà a realizzare una struttura sbagliata.
L'enfasi viene spostata da computazione a rappresentazione (più o meno astratta) sul quale il software deve agire

#### Metodi di progettazione software

Il software può essere visto come un insieme di scatole, nelle quali entrano ed escono dati.

Viene utilizzato l'**UML** (*unified modeling language*), uno standard che contiene un insieme di linguaggi grafici per realizzare un diagramma delle classi e degli oggetti, ottenendo una rappresentazione grafica della programmazione.

Oggetti in UML
All'interno dell'UML, la relazione oggetto-classe è simile a elemento-insieme

Classe  | Insieme
--------| -------
Oggetto | Elemento

Gli oggetti risultano essere elementi del dominio con vita propria indipendente con identificatore e istanza.

La parte grafica in UML non è arbitraria ma unificata, ovvero vengono utilizzate convenzioni per rappresentare determinati elementi del programma.

<img src="https://github.com/davidegagliardi/OOP/blob/master/ObjectUML.png" />

### Differenze valore / puntatore / riferimento

* **Passaggio per valore**: il valore di una variabile viene copiato in una struttura stack. Successivamente la funzione recupera il dato.
* **Passaggio per indirizzo**: viene copiato l’indirizzo della variabile in modo esplicito.
Il passaggio per indirizzo viene utilizzato se la variabile è "grande".
* **Passaggio per riferimento** (esclusivo del c++):  alla funzione viene passato l’indirizzo e non il valore dell’argomento. Questo approccio richiede meno memoria rispetto alla chiamata per valore, e soprattutto consente di modificare il valore delle variabili che sono ad un livello di visibilità (scope) esterno alla funzione o al metodo.

//Conviene passare per indirizzo se la variabile è grande, altrimenti va bene /per valore perché copio solo la variabile.
P. riferimento: la variabile grande passa così per non spostare molti dati nella memoria. Si tende a non fare la copia.

#### Operatore “++”
Può essere pre-fisso (`++i`) o post-fisso (`i++`).

Nel caso di incremento pre-fisso, la variabile verrà incrementata nello stesso ciclo:
```
int i = 5;
cout << "Il valore di i e' " <<  ++i;

//L'output del programma sarà "Il valore di i è 6"
```
Nel caso di operatore post fisso, la variabile verrà incrementata nel ciclo successivo:
```
int i = 5;
cout << "Il valore di i e' " <<  i++;

//L'output del programma sarà "Il valore di i è 5"
```

Nel primo caso il valore viene incrementato e restituito prima dell’assegnazione (non si vede sul risultato nel passaggio a valori??!?). E’ un operatore unario, valore restituito prima dell’incremento (i++  i). Nel puntatore la variabile rimane la medesima ma viene incrementato il puntatore. Il risultato, a differenza di prima si vede.
Prefisso si vede subito, post fisso dopo.

Con new alloco un puntatore di memoria: alloco la memoria in modo dinamico. Non bisogna cancellare l’indirizzo di memoria allocato, se non faccio il delete cresce l’occupazione del programma nella memoria.


Costruttori: quando costruisco una classe vuota è come se io facessi una definizione astratta perché non è detto che il compilatore allochi una memoria, come ad esempio il typedef. Se istanzio una classe ho un’allocazione di memoria (7:40). Se ho una classe vuota e l’istanza A non so cosa ci sia in questo momento. Risultato, rispetto a quello che c’era prima in memoria vengono aggiunte due cose: un puntatore this che punta dove la variabile è (punta a se stessa) e viene allocato un altro puntatore che punta dove ci sono i metodi di A. Punta i costruttori che ci sono sempre (default, 0 parametri, distruttore, costruttore di copia, operatore di assegnazione). Questo è a livello di memoria (lo fa il compilatore).

Header
Dichiarazione con cui si dichiarano il nome che il compilatore usa per chiamare il metodo (che è l’unico nel programma).
Costruttore: metodo che viene chiamato quando si definisce un’istanza A::A() è chiamato con A e a; gli attributi in classe vanno allocati nella memoria (non memoria dinamica) . 09:40

Distruttore: metodo che viene chiamato quando l’istanza è deallocata. Per esempio A::~A().
E’ in grado di mettere le cose in ordine prima che l’informazione dell’istanza venga perduta per sempre. E’ un puntatore ad una classe di fatto. Il costruttore di una classe vuota inizializza, però lo utilizziamo ad esempio quando in una classe abbiamo un’istanza di un’altra classe, creo un richiamo ad una classe sopra il blocco, richiamando il costruttore dell’altra classe in modo da inizializzare l’attributo presente nella classe successiva. Solitamente lo si fa per ereditarietà. Il distruttore non fa nulla. Prima eseguirà sul codice e poi chiamerà gli attributi infatti prima chiama, poi esegue il codice e infine metterà un “+”.  Minuto 12:00 cazzo fa?

Passaggio per valore: un’area di memoria di “a” viene presa, copiata e inizializzata con il costruttore di copia. Di solito quando ho una nuova istanza devo inizializzarla.
Il costruttore di copia non chiama né costruttore di default ne distruttore. E’ un costruttore a se.
Prende qualcosa da una cella di memoria e lo copia in un’altra.
This punta a se stesso, se però in mezzo ho fatto un costruttore di copia una cella di memoria viene utilizzata per questo costruttore di copia e this punterà sempre a te stesso, solamente che non ho celle contigue.

Fa una copia dei valori campo per campo.

Il costruttore di default viene eliminato se ridefinisco costruttore con almeno un parametro. Posso fare una copia profonda che quando parte dalla memoria dinamica deve essere copiata nell’istanza (non sempre nel caso di dinamica però).
Copia superficiale viene fatta valore per valore degli attributi (costruttore copia / valore di assegnazione 15:00).

Copia attributo per attributo
This rimane uguale, che è la proprietà di singola istanza e non copia puntatore a metodi.

Il c++ cerca di risolvere tutte le istruzioni che possono essere simili o possono ricondursi a qualcosa, se ho un metodo/funzione e aggiungo explicit davanti evito questa cosa. Il c++ interpreta il costruttore a 1 parametro come se fosse un convertitore di tipo. ????
Spiegare meglio
