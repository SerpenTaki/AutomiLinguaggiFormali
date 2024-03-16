- Sono il più semplice *modello computazionale*
- Dispongono di una quantità di memoria *finita*
- Gli automi a stati finiti sono usati come *modello* per.
	- Software per la progettazione di circuiti digitali
	- Analizzatori lessicali di un compilatore
	- Ricerca di parole chiave in un file o sul web
	- Software per verificare sistemi a stati finiti come protocolli di comunicazione
## Alfabeti e linguaggi
Per rappresentare in maniera precisa un automa dobbiamo definire dei concetti base:
- Che cos'è un *alfabeto* (di simboli / messaggi / azioni)
- Che cos'è un *linguaggio formale*
- Che cos'è un *Automa a stati finiti deterministico*
- Che vuol dire che un automa *accetta* un linguaggio
### Alfabeto
**Alfabeto:** Insieme finito e non vuoto di simboli
- **Esempio**: $\sum = \{0,1\}$ alfabeto binario
- **Esempio:** $\sum = \{ a,b,c,...,z\}$ insieme di tutte le lettere minuscole
- **Esempio:** Insieme di tutti i caratteri ASCII
**Stringa:** (o *parola*) Sequenza finita di simboli da un alfabeto $\sum$ e.g. 0011001
**Stringa vuota**: La stringa con zero occorrenze di simboli da $\sum$
- La *stringa vuota* è denotata con $\epsilon$
**Lunghezza di una stringa:** Numero di simboli nella stringa
- $|w|$ denota la lunghezza della stringa $w$
- $|0110| = 4$, $|\epsilon| = 0$
#### Potenze di un alfabeto
$\sum^k =$ insieme delle stringhe di lunghezza $k$ con simboli da $\sum$
- Esempio: $\sum = \{0,1\}$
	- $\sum^0 = \{\epsilon\}$
	- $\sum^1 = \{0,1\}$
	- $\sum^2 = \{00,01,11\}$
L'insieme di *tutte le stringhe* su $\sum$ è denotato da $\sum^*$
$\sum^* = \bigcup^{\infty}_{i=0} \sum^i$ 
### Linguaggio
Dato un alfabeto $\sum$, chiamiamo linguaggio ogni sottoinsieme $L\subseteq \sum^*$
*Esempi*
- Insieme delle parole italiane
- Insieme dei programmi C sintatticamente corretti
- Insieme delle stringhe costituite da $n$ zeri e seguite da $n$ uni
- il *linguaggio vuoto* $\oslash$  non contiene nessuna parola

# DFA
**Automa a stati finiti Deterministico**
--
È una quintupla $A = (Q, \sum, \delta, q_0, F)$
- $Q$ è un insieme finito di *stati*
- $\sum$ è un *alfabeto finito* (= simboli in input)
- $\delta : Q \times \sum \mapsto Q$ è una *funzione di transizione*
- $q_0 \in Q$ è lo *stato iniziale*
- $F \subseteq Q$ è un insieme di *stati finali*
Possiamo rappresentare gli automi sia come *diagramma di transizione* che come *tabella di transizione*

**ESEMPIO**:
*costruiamo un automa A che accetta il linguaggio delle stringhe con 01 come sottostringa*
- **Automa come _diagramma di transizione_:**
![[Screenshot 2024-03-16 alle 21.48.55.png]]
- **Automa come _tabella di transizione_**

|                   | 0     | 1     |
| ----------------- | ----- | ----- |
| $\rightarrow q_0$ | $q_1$ | $q_0$ |
| $q_1$             | $q_1$ | $q_2$ |
| $*q_2$            | $q_2$ | $q_2$ |
 ![[Screenshot 2024-03-16 alle 21.52.22.png]]
 Automa che accetta tutte le parole che finiscono con 1
## Computazione di un DFA
- Data una parola $w = w_1w_2...w_n$ la *computazione* dell'automa A con input $w$ è una sequenza di stati $r_0r_1...r_n$ che rispetta *2 condizioni:*
	1. $r_0 = q_0$ (inizia dallo stato iniziale)
	2. $\delta(r_i, w_i+1) = r_{i+1}$ per ogni $i=0,...,n-1$ (rispetta la funzione di transizione)
- Diciamo che la computazione *accetta* la parola $w$ se:
	3. $r_n \in F$ (la computazione *termina in uno stato finale*)
**QUINDI**:
- Un **_DFA_** A accetta la parola $w$ se la computazione accetta $w$
- Formalmente, il *linguaggio accettato* da A è
		$L(A) = \{w \in  \sum^* | A$ accetta $w\}$
- I linguaggi accettati da automi a stati finiti sono detti [[Linguaggi regolari]]
