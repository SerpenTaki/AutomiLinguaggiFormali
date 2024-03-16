- **Intersezione**:
$L \cap M = \{ w : w \in L$ e $w \in M \}$
- **Unione**:
$L \cup M = \{ w : w \in L$ oppure $w \in M \}$
- **Complemento:**
$\overline{L} = \{ w : w \notin L\}$ 
- **Concatenazione**
$L.M = \{ uv : u \in L$ e $v \in M \}$
- **Chiusura (_o Star_) di Kleene:**
$L^* = \{ w_1 w_2 ... w_k : k \geq 0$ e ogni $w_i \in L\}$

![[Screenshot 2024-03-16 alle 22.46.01.png]]
![[Screenshot 2024-03-16 alle 22.46.16.png]]
![[Screenshot 2024-03-16 alle 22.47.08.png]]
## Proprietà di chiusura:
Se $L$ e $M$ sono linguaggi regolari, allora:
- *Intersezione:* $L \cap M$ è un linguaggio regolare?
- *Unione* $L \cup M$ è un linguaggio regolare?
- *Complemento* $\overline{L}$ è un linguaggio regolare?
- *Concatenzazione* $L.M$ è un linguaggio regolare?
- *Star di Kleene* $L^*$ è un linguaggio regolare?
### Chiusura per intersezione
**Theorem**: Se L e M sono regolari, allora anche $L \cap M$ è un linguaggio regolare.
**Dimostrazione:**
- Sia $L$ il linguaggio di:
		$A_L = (Q_L, \sum, \delta_L, q_L, F_L)$
- e $M$ il linguaggio di:
		$A_M = (Q_M, \sum, \delta_M, q_M, F_M)$
Possiamo assumere che entrambi gli automi siano *deterministici*. Costruiremo un automa che simula $A_L$ e $A_M$ in parallelo, e accetta se e solo se sia $A_L$ che $A_M$ accettano.

Se $A_L$ va dallo stato $p$ allo stato $s$ leggendo $a$, e $A_M$ va dallo stato $q$ allo stato $t$ leggendo $a$, allora $A_{L\cap M}$ andrà dallo stato $(p,q)$ allo stato $(s,t)$ leggendo $a$.
$A_{L \cap M}$ accetta una parola solo quando *sia $A_L$ che $A_M$ accettano*
$\iff$
$A_{L \cap M}$ accetta solo quando $(p,q)$ è una *coppia di stati finali*
*Formalmente:*
$A_{L \cap M} = ( Q_L \times Q_M, \sum, \delta_{L \cap M}, (q_L, q_M), F_L \times F_M)$ dove $\delta_{L \cup M} ((p,q),a) = (\delta_L(p,a), \delta_M(q,a))$ 

*Leggere il libro*