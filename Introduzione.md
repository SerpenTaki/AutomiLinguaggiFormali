# Problemi
Per descrivere un *problema* bisogna specificare:
- Insieme dei possibili Input
- Insieme dei possibili Output
- La relazione tra Input e Output
![[Screenshot 2024-03-16 alle 21.01.23.png]]

**Algoritmo**: procedura meccanica che esegue delle computazioni (*e può essere eseguita da un calcolatore*)
- Un *algoritmo risolve* un dato problema se:
	- Per ogni input, il calcolo dell'algoritmo si interrompe dopo un numero finito di passaggi
	- Per ogni input, l'algoritmo produce un output corretto
**Correttezza** di un algoritmo:
- Verificare che l'algoritmo risolva realmente il problema dato
**Complessità computazionale** di un algoritmo:
- **complessità temporale**: come varia il tempo di esecuzione rispettto alla dimensione dei dati di input
- **complessità spaziale**: come varia la quantità di memoria utilizzata rispetto alla dimensione dei dati di input
# Linguaggi Formali
- Astrazione della nozione di problema
- I problemi sono espressi come *linguaggi* (insieme di stringhe)
	- Le soluzioni determinano se una determinata stringa è nell'insieme o no
		- ES.*un certo intero $n$ è un numero primo?*
- Oppure, come *trasformazioni tra linguaggi*
	- Le soluzioni trasformano la stringa di input in una stringa di output
		- ES: *quanto fa $3+5$?*
- Quindi in sostanza tutti i processi computazionali possono essere ridotti ad uno tra:
	- Determinazione dell'*appartenenza* a un insieme (di stringhe)
	- *Mappatura* tra insiemi (di stringhe)
- Formalizzeremo il concetto di computazione meccanica:
	- Dando una definizione precisa del termine "algoritmo"
	- Caratterizzando i problemi che sono o non sono adatti per essere risolti da un calcolatore
# Automi
- Gli *automi* sono dispositivi matematici astratti che possono:
	- Determinare l'appartenenza di una stringa ad un insieme di stringhe
	- Trasformare una stringa in un'altra stringa
- Hanno tutti gli *aspetti* di un computer
- Il tipo di **memoria** è cruciale:
	- memoria finita
	- memoria infinita:
		- con accesso limitato
		- con accesso illimitato
- Abbiamo diversi tipi di autommi per diversi classi di linguaggi
- I diversi tipi di automi si differenziano per
	- La quantità di memoria (finita vs infinita)
	- Il tipo di accesso alla memoria (limitato vs illimitato)
