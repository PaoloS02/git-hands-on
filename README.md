# git-hands-on

Intro
=====

Installa git sul pc.
Sul mac se ho capito bene basta che tu provi ad eseguire git. Ricorda che git si usa da terminale.
Quindi prova:

% git --version

A quel punto non so se ti propone di installarlo se non ce l'hai o che.


Inizializza un repository git
=============================

Crea una nuova cartella, entraci e digita:

% git init

Git crea una sottocartella "nascosta" .git/ dove mettera' tutte le informazioni che gli servono per tracciare e gestire la storia del tuo progetto.
Da questo momento git individuera' ogni modifica che fai al contenuto della cartella. Le modifiche che git vede sono le aggiunte di file nella cartella oppure le modifiche (salvate) di file gia' esistenti nella cartella.

Primo commit
============

Digita:

% git status

ti mostra lo stato del repository o cartella di lavoro. Se dice "clean" vuol dire che non c'e' niente di nuovo.

Crea un file di testo.
Ora riguarda lo stato.
'git status' ora ti dira' che c'e' un file nuovo untracked.
Untracked si riferisce ai cambiamenti che git percepisce nella cartella ma che tu non hai ancora detto a git di 'segnarsi'.
Quindi attenzione: git vede in automatico i cambiamenti, ma ha bisogno che tu gli dica quali cambiamenti tracciare prima che tu possa dire a git di fare un commit di quei cambiamenti e inserirlo nella storia.

Per far tracciare a git un cambiamento usiamo:

% git add

Quindi se hai creato il file di testo README per esempio dovrai digitare

% git add README

Se ora guardi lo stato di nuovo vedi che e' cambiato. Dovrebbe essere passato dal rosso dei caratteri al verde. (poi non so se per mac fa colori diversi).
Se avessi creato 3 file e tracciato solo uno con git-add avresti visto due file scritti in rosso e uno in verde.

Comunque, ora che il cambiamento e' tracciato puoi creare il commit, il piccolo record, fotogramma, come si vuol dire, da aggiungere alla storia del progetto.

% git commit

Apre l'editor di git. vedrai che ci sono dei commenti che cominciano con #. Tu devi solo scrivere il messaggio di commit, la descrizione del tuo cambiamento (nel tuo caso puo' essere banalmente "Initial commit.") e poi per salvare e chiudere fai ctrl+x, e quando ti chiede conferma digiti Y e invio.

Se vuoi far prima senza aprire l'editor puoi fare

% git commit -m "Initial commit."

Ora se guardi di nuovo lo stato vedrai che la cartella e' tornata "clean" come all'inizio.
Se invece fai:

% git log

Puoi rivedere il messaggio del tuo commit, con anche hash, data, nome dell'autore ecc...
git-log mostra la storia del ramo corrente del progetto su cui sei.
Una volta che hai almeno due commit nella tua storia puoi vedere le diff, cioe' le modifiche di specifici commit nella storia.

% git diff hash1 hash2

dove hash1 e' l'hash del commit precedente a quello che vuoi vedere, mentre hash2 e' l'hash del commit che vuoi vedere.
Con un commit solo si puo' fare ma e' scomod perche' git non ha una versione del tuo progetto registrata da te precedente al commit iniziale con cui confrontare. Per questo e' bene fare come commit iniziale un commit neutro, dove non ci siano cambiamenti rilevanti, perche' se li vuoi vedere devi fare cose come:

% git diff 4b825dc642cb6eb9a060e54bf8d69288fbee4904 HEAD

dove 4b825dc642cb6eb9a060e54bf8d69288fbee4904 e' l'hash dell'albero vuoto di git. Il livello 0 diciamo. Insomma, non e' proibito. E' scomodo.

Altrimenti puoi usare

% git show HEAD

HEAD e' l'etichetta del commit su cui poggi. Il punto dell'albero della storia del progetto su cui stai al momento. La versione corrente del tuo progetto.
git-show mostra il commit e il messaggio e si puo' usare anche col primo commit.

