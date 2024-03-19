- Un FA (NFA "[[Automi a Stati Non Deterministici]]" o DFA "[[Automi a Stati Non Deterministici]]) è un metodo per costruire una macchina che riconosce linguaggi regolari
- Una *espressione regolare* è un modo dichiarativo per descrivere un linguaggio regolare
- Esempio: 01* + 10*
- Le espressioni regolari sono usate ad esempio in:
	- comandi UNIX (*grep*)
	- strumenti per l'analisi lessicale di UNIX (`lex` *Lexical analyzer generator*) e `flex`(*Fast Lex*)
	- editor di testo
# Espressioni regolari
sono costruite utilizzando:
- un insieme di *costanti* di base:
	- $\epsilon$ per la stringa vuota
	- $\oslash$ per il linguaggio vuoto
	- $a, b,...$ per i simboli $a,b,... \in \sum$
- collegati da *operatori:*
	- $+$ per l'unione
	- $.$ per la concatenazione
	- $*$ per la chiusura di Kleene
- Raggrupati usando le *parentesi* $()$
Se $E$ è un espressione regolare, allora $L(E)$ è il *linguaggio rappresentato da $E$*. La definizione di $L(E)$ è induttiva:
- **Caso Base**:
	- $L(\epsilon) = \{ \epsilon \}$
	- $L(\oslash) = \oslash$
	- $L(a) = \{a\}$
- **Caso induttivo:**
	- $L(E + F) = L(E) \cup L(F)$
	- $L(EF) = L(E).L(F)$
	- $L(E*) = L(E)^*$
	- $L((E)) = L(E)$
**ESEMPIO**:
$L=\{w \in \{0,1\}^* : 0$ e $1$ alternati in $w \}$
$(01)^* + (10)^* + 1(01)^* + 0(10)^*$ oppure $(\epsilon +1)(01)^*(\epsilon+0)$
### Precedenza
Come per le espressioni aritmetiche, anche per le espressioni regolari ci sono delle *regole di precedenza* degli operatori
1. chiusura di Kleene
2. Concatenazione (punto)
3. Unione
**ESEMPIO**:
$01^*+1$ è raggrupato in $(0(1)^*)+1$
e denota un linguaggio *diverso* da $(01)^*+1$
# Conversione per eliminazione di stati
- La procedura che vedremo è in grado di convertire un *qualsiasi automa* (DFA o NFA) in una *espressione regolare* equivalente
- Si procede per *eliminazione di stati*
- Quando uno stato $q$ viene eliminato i cammini che passano per $q$ scompaiono
- Si aggiungono nuove *transizioni etichettate con espressioni regolari* che rappresentano i cammini eliminati
- alla fine otteniamo un'espressione regolare che rappresenta *tutti i cammini* dallo stato iniziale ad uno stato finale
	-> cioè il *linguaggio riconosciuto dall'automa*

![[Screenshot 2024-03-19 alle 16.40.07.png]]
# Definizione formale di GNFA
Un Automa a Stati Finiti Non Deterministico Generalizzato (GNFA) è una quintupla:
	$A=(Q, \sum, \delta, q_{start}, q_{accept})$
- Q è un insieme finito di *stati*
- $\sum$ è un *albero finito*
- $\delta : Q \backslash \{q_{accept}\} \times Q \backslash \mapsto R$ è una *funzione di transizione* che prende in input *2 stati* e restituisce una *espressione regolare* su $\sum$
- $q_{start} \in Q$ è lo *stato iniziale*
- $q_{accept}$ è lo *stato finale*
## Computazione di un GNFA
- Data una parola $w= w_1 w_2 ... w_m$ , dove $w_i \in \sum^*$
- Una *computazione* di un GNFA $A$ con input $w$ è una sequenza di stati $r_0r_1...r_m$ che rispetta *2 condizioni*:
	1. $r_0 = q_{start}$ (inizia dallo stato iniziale)
	2. Per ogni $i, w_i \in L(R_i), dove R_i = \delta(r_{i-1}, r_i)$ (*rispetta la funzione di transizione*)
- Una computazione *accetta* la parola $w$ se *termina nello stato finale* ($r_m = q_{accept}$)
![[Screenshot 2024-03-19 alle 16.55.10.png]]
![[Screenshot 2024-03-19 alle 16.57.00.png]]
![[Screenshot 2024-03-19 alle 16.57.13.png]]
### Algoritmo di conversione:
**`Convet(A)`**:
1. Sia $k$ il numero di stati di $A$
2. Se $k=2$, ritorna l'espressione $R$ che collega $q_{start}$ con $q_{accept}$
3. Se $k > 2$, scegli $q_{rip} \in Q \backslash \{q_{start}, q_{accept}\}$ e costruisci un GNFA $A' = (Q',\sum, \delta ', q_{start}, q_{accept})$ come segue:
	- $Q' = Q \backslash \{q_{rip}\}$
	- per ogni $q_i \in Q' \backslash \{q_{accept}\}, q_j \in Q' \backslash \{q_{start}\}$, sia $\delta '(q_i,q_j) = (R_1(R_2)*R_3)+R_4$ dove $R_1 = \delta (q_i,q_{rip}), R_2 = \delta (q_{rip}, q_{rip}), R_3 = \delta (q_{rip}, q_j)$ e $R_4=\delta (q_i, q_j)$
4. Ritorna il risultato calcolato da `Convet(A')`
