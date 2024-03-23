Di quanti stati necessita l'automa che riconoscere linguaggio $\{0^n1^n|n\geq0\}$?
Occorrono $2n$ stati per poter riconoscere il linguaggio. Essendo $n$ infinito non è possibile determinare un numero finito di stati, pertanto il linguaggio $\{0^n1^n|n\geq0\}$ non è regolare, proprio perché non può essere riconosciuto da un automa a stati finiti. 

# Dimostrazione

È necessario ragionare *per assurdo*, in quanto siamo costretti a dimostrare che non esiste un automa a stati finiti che riconosce un linguaggio che ipotizziamo essere non regolare. 
Supponiamo che  $L_{01}=\{0^n1^n|n\geq0\}$ sia regolare, allora esiste un DFA A che accetta $L_{01}$ con $k$stati. 
Cerchiamo ora di dimostrare che esiste una parola appartenente a $L_{01}$ che non viene riconosciuta dall'automa DFA.
L'automa segue una computazione $r_0, r_1, r_2,\dots,r_k$ ovvero di lunghezza $k+1$, questo comporta che all'interno della sequenza c'è uno stato che si ripete, supponiamo che si tratti di  $r_i =r_j$ per qualche $a$.
Posso sfruttare questo fatto per far sbagliare l'automa:
considero la parola $0^i1^i$, la computazione ha la forma $$r_0, r_1, \dots, r_i, s_1, \dots, s_i$$
$s_i$ è uno stato finale? Sì, $s_i$ deve essere finale. 
Cosa succede se a questo automa forniamo in input la parola $0^j1^i$ ? 
Abbiamo detto che $r_j=r_i$quindi l'automa terminerà nello stesso stato finale $s_i$ e dunque verrebbe riconosciuta una parola che non appartiene a $L_{01}$.

## Riassunto
- supponiamo che $l_{0}=\{0^n1^n | n \geq 0\}$ 
- cazzo ha girato slide
- ...

- cosa succede quando l; automa $A$ legge $1^i$ partendo da $q$ 
- se l'automa finisce la lettura in uno stato finale
	- allora accetta, sbagliando la parola $0^j1^j$ 
- se l'automa finisce la lettura in uno stato non finale
	- allora rifiuta sbagliando la parola $0^i1^i$ 
- in entrambi i casi abbiamo ingannato l'automa, quindi $L_{01}$ *non può essere regolare*

# Proprietà dei linguaggi regolari
Possono essere utilizzate per dimostrare che un DFA effettua un loop per accettare un linguaggio regolare. La dimostrazione è più facile rispetto a quella precedente. 
## Pumping Lemma 
Sia $L$ un linguaggio regolare. Allora
- _esiste una lunghezza_ $k>0$ tale che 
- _ogni parola_ $w\in L$ di lunghezza $|w|\geq k$ 
- _può essere spezzata_ in $w =xyz$ tale che 
	1. $y\neq \epsilon$ (il secondo pezzo è non vuoto)
	2. $|xy|\geq k$ (i primi due pezzi sono lunghi al max $k$)
	3. $\forall i \geq 0, xy^iz\in L$ (possiamo "pompare" $y$ rimandandolo in $L$)
### Dimostrazione
- Supponiamo che $L$ sia un linguaggio regolare
- Allora è riconosciuto da un DFA con, supponiamo, $k$ stati
- Consideriamo una parola $w = a_1, a_2, \dots, a_n\in L$ di lunghezza $n\geq k$ 
- Consideriamo gli stati nella computazione di $A$ per $w$ 
$$p_0, p_1, p_2,\dots p_k\dots p_n$$
- Siccome in $p_0, p_1,\dots p_k$ ci sono $k+1$ stati ne esiste uno che si ripete:
Esistono $l< m$ tali che $p_l=p_m$ e $m \leq k$ 

#### Pumping lemma come gioco 
Esiste una strategia che ci consente di vincere sempre su un certo linguaggio. 
1. $\exists k>o$  (giocatore 1 sceglie la dimensione di $k$)
2. $\forall w\in L, |w|\geq k$ (giocatore 2 sceglie una parola)
3. $\exists xyz| w= xyz$
	$y\neq \epsilon$ 
	$|xy| \leq k$ (giocatore 1 sceglie come partizionare la parola)
4.	$\forall i\geq 0 xy^iz\in L$ (giocatore 2 sceglie una potenza affinché la condizione sia verificata)
Se giocatore 2 vince allora il linguaggio non è regolare. 

### Esistono linguaggi non regolari che rispettano il Pumping Lemma

**Sia $L_{ab}$ il linguaggio delle stringhe sull'alfabeto $(a,b)$ dove il numero di $a$ è uguale al numero di $b$. $L_{ab}$ è regolare?**
Per assurdo ipotizzo $L_{ab}$ regolare. 
Se lo è, allora rispetta il Pumping Lemma $\rightarrow$ deve esistere una lunghezza $k>0$ che rende vero il Pumping Lemma.
Consideriamo la parola $w=a^kb^k$ , $w$ appartiene al linguaggio e $|w|>k$ .
Per ogni suddivisione $w\in xyz$ dove $y\neq \varnothing$ e $|xy|\leq k$ 
$$x = a^P$$
$$y = a^Q$$
$$z = a^{K-P-Q}b^K$$
Se prendiamo come esponente $i=2$ , $xy^2z=a^Pa^{2Q}a^{K-P-Q}b^K= a^{Q+K}b^K$ la parola non fa parte del linguaggio.
**Conclusione: per assurdo non è regolare.**



**Il linguaggio $L_{rev} = \{ww^R:w \in\{a,b\}*\}$ è regolare?**

$w^R = w$ scritto alla rovesciao
$w = w_1, w_2, \dots, w_k$ 
$w^R=w_n, w_{n-1}, \dots, w_1$ 

1. Suppongo $L_{rev}$ sia regolare,allora esiste $k>0$ che rende vero il Pumping Lemma
2. considero la parola $w=a^kb^2a^k$ 
3. Per ogni suddivisione di $xyz$ dove $y\neq \epsilon$ e $|xy|\leq k$ 
$$x = a^P$$
$$y = a^Q$$
$$z = a^{K-P-Q}b^2a^K$$
Se prendiamo come esponente $i=2$ , $xy^2z=a^Pa^{2Q}a^{K-P-Q}b^2a^K= a^{Q+K}b^2a^K$ la parola non fa parte del linguaggio.
**Conclusione: per assurdo non è regolare.**


**il linguaggio $L_{p} = \{1^p: p$  è primo$\}$ è regolare?**
1. Assumo che $L_p$ sia regolare e che $k>0$ sia la lunghezza che rende vero il Pumping Lemma. 
2. Considero $w=1ĵ$ dove $j$ è il primo numero primo $>k$ 
3. Per ogni suddivisione $w=xyz$ dove $y\neq \varnothing$ e $|xy| \leq k$ 
	1. $x=1^P$ 
	2. $y = 1^Q$ 
	3. $z=1^{J-P-Q}$ dove $Q>0$ e $P+Q \leq k$ 

$i=2$ 
$xy^2z = 1^P1^{2Q}1^{J-P-Q}=1^{Q+J}$

$i=2J$
$xy^{2J}z = 1^P1^{2jQ}1^{J-P-Q}=1^{(2J)Q+J-Q}$
$= 1^{(2J-1)Q+J} = 1^{(Q+1)J} \not\in L_p$ 
La parola non è contenuta nel linguaggio in quanto la sua lunghezza è un numero scomponibile in fattori. 


