$3.2.4\ EXERCISE[\star\ \star]$: How many elements does $S_3$ have?

$Solution$:
Since $S_0 = \varnothing$, and $S_1 = \{true,false,0\}$, there is $$|S_1|=3$$
And $S_2=\{true,false,0\}\cup\{succ\ t_1,pred\ t_1,iszero\ t_1\ |\ t_1\in S_1\}\cup\{if\ t_1\ then\ t_2\ else\ t_3\ |\ t_1,t_2,t_3\in S_1\}$.
So$$|S_2|=3+3\cdot|S_1|+|S_1|^3=3+3\cdot3+3^3=3+9+27=39$$
And then we can get $$S_3=\{true,false,0\}\cup\{succ\ t_1,pred\ t_1,iszero\ t_1\ |\ t_1\in S_2\}\cup\{if\ t_1\ then\ t_2\ else\ t_3\ |\ t_1,t_2,t_3\in S_2\}$$
So $$|S_3|=3+3\cdot|S_2|+|S_2|^3$$
and replace $|S_2|$ with 39:$$|S_3|=3+3\cdot39+39^3=59439$$
Hence $$\boxed{|S_3|=59439}$$

---
$3.2.5\ EXERCISE[\star\ \star]$: Show that the sets $S_i$ are *cumulative* -- that is, that for each $i$ we have $S_i\sube S_{i+1}$.

$Proof:$
We proceed by induction on $i$:

When $i=0$, there is $S_0=\varnothing$, so it is trivially true that $S_0\sube S_1$.
Assume for some $i$ that $$S_i\sube S_{i+1}$$
and the target we need to prove is $$S_{i+1}\sube S_{i+2}$$
And for all $x\in S_{i+1}$, there is only **three** possible cases for it:
***Case1: x is a constant:***
so $$x\in \{true,false,0\}$$
and by definition, $$\{true,false,0\}\sube S_{i+2}$$
hence there is $$x\in S_{i+2}$$
***Case2: x is in the form of $succ\ t$, $pred\ t$ or $\ iszero\ t$:***
in this case, $x$ is $$succ\ t_1\quad\text{or}\quad pred\ t_1\quad\text{or}\quad iszero\ t_1$$
and $$t_1\in S_i$$
From the assumption $S_i\sube S_{i+1}$, we can get that $$t_1\in S_{i+1}$$
and by the definition of $S_{i+2}$ that $\forall t_1\in S_{i+1}\text{, the }succ\ t_1,pred\ t_1\text{ and }iszero\ t_1\text{ all belongs to }S_{i+2}$, there is $$x\in S_{i+2}$$
***Case3: x is $if$ expression***
and in this case, there is $$x = if\ t_1\ then\ t_2\ else\ t_3\text{ , the } t_1\text{,}t_2\text{,}t_3\in S_{i}$$
and it is obvious that all of them belong to $S_{i+1}$:$$t_1,t_2,t_3\in S_{i+1}$$
and by the definition, we can construct $if$ expression with elements from $S_{i+1}$, so there is $$x\in S_{i+2}$$
Hence, for all $x\in S_{i+1}\text{, }x\in S_{i+2}$, which means $$\boxed{S_{i+1}\sube S_{i+2}}$$

> Hence $$S_0\sube S_1\sube S_2\sube S_3\sube\cdots$$
> and therefore $$S=\bigcup_i S_i$$
> we may also write: $$S:=\lim_{i\rightarrow\infty}S_i$$
> And we can know that ***if there is a constructor $op$, if $S_0=\varnothing\text{ and }S_{i+1}:=Base\cup\{op(t_1,\cdots,t_n)|t_1,\cdots,t_n\in S_i\}$, there will always be $S_i\sube S_{i+1}$***
