# Aufgabe 1

## Problemstellung

Wir betrachten eine autonome Differentialgleichung der Form:

$$
y'(t) = f(y(t))
$$

wobei $f: X \to \mathbb{R}$ eine Funktion ist und $X \subseteq 
\mathbb{R}$. Wir wollen zeigen, dass wenn $y:(a, b) \to X$ eine 
Lösung dieser Differentialgleichung ist, dann ist auch die zeitverschobene 
Funktion

$$
z(t) = y(t + \alpha)
$$


für jedes $\alpha \in \mathbb{R}$ eine Lösung auf dem Intervall 
$(a - \alpha, b - \alpha)$ ist.

## Lösung

**Beweis:**

Um zu zeigen, dass $z(t)$ eine Lösung der Differentialgleichung ist, müssen wir überprüfen, ob sie die Gleichung erfüllt:

1.  **Definitionsbereich:** Da $y(t)$ auf dem Intervall $(a, b)$ 
definiert ist, ist $z(t) = y(t + \alpha)$ auf dem Intervall $(a 
-\alpha, b - \alpha)$ definiert.

2.  **Ableitung von $z(t)$ :** Die Ableitung von $z(t)$ nach der Kettenregel ist:

$$
z'(t) = y'(t + \alpha) \cdot 1 = y'(t + \alpha) 
$$

3.  **Einsetzen in die Differentialgleichung:** Setzen wir $z(t)$ 
und $z'(t)$ in die Differentialgleichung ein:

$$
z'(t) = f(z(t)) \\
y'(t + \alpha) = f(y(t + \alpha)) 
$$

Da $y(t)$ eine Lösung der Differentialgleichung ist, gilt 
$y'(t) = f(y(t))$ für alle $t \in (a, b)$. Da $t + \alpha$ im 
Intervall $(a, b)$ liegt, wenn $t$ im Intervall $(a - \alpha, 
b - \alpha)$ liegt, gilt auch:

$$
y'(t + \alpha) = f(y(t + \alpha))
$$


Dies zeigt, dass $z(t)$ die Differentialgleichung erfüllt.

**Schlussfolgerung:**

Da $z(t)$ den Definitionsbereich erfüllt und die Differentialgleichung 
erfüllt, ist $z(t) = y(t + \alpha)$ eine Lösung der autonomen 
Differentialgleichung auf dem Intervall $(a - \alpha, b - \alpha)$.

**In einfachen Worten:**

Wenn du eine Lösung einer autonomen Differentialgleichung hast, 
kannst du diese Lösung zeitlich verschieben (nach vorne oder 
hinten), und die verschobene Funktion ist immer noch eine Lösung. 
Dies liegt daran, dass die rechte Seite der Differentialgleichung 
nicht explizit von der Zeit abhängt.

# Aufgabe 2

## Problemstellung

Gegeben sei das Anfangswertproblem (AWP):

$$
y'(t) = F(t, y(t)) \quad \text{für } t > 0, \quad y(0) = y_0
$$

## Lösung

### a. Nachweis für $y(t)=\frac{1}{(1+t^2)}$:

1.  **Ableitung:** Berechnen wir die Ableitung von $y(t)$:

$$
y'(t) = \frac{-2t}{(1 + t^2)^2}
$$

2.  **Einsetzen in die Differentialgleichung:** Setzen wir $y(t)$ und $y'(t)$ in die Differentialgleichung ein:

$$
\frac{-2t}{(1 + t^2)^2} = -2t \left(\frac{1}{1 + t^2}\right)^2
$$


Die Gleichung ist erfüllt.

3.  **Anfangsbedingung:** Überprüfen wir die Anfangsbedingung:

$$
y(0) = \frac{1}{1 + 0^2} = 1 = y_0
$$

Die Anfangsbedingung ist erfüllt.

**Fazit:**

Die Funktion $y(t) = \frac{1}{1 + t^2}$ ist eine Lösung des AWP 
für $F(t, x) = -2tx^2$ und $y_0 = 1$.

### b. Nachweis für $y(t) = e^{-2t} + 1$:

1.  **Ableitung:** Berechnen wir die Ableitung von y(t):
$$
y'(t) = -2e^(-2t)
$$

2.  **Einsetzen in die Differentialgleichung:** Setzen wir $y(t)$ und $y'(t)$
in die Differentialgleichung ein:

$$
-2e^{-2t} \quad = 2 - 2(e^{-2t} + 1)\\
\quad = \quad 2 - 2e^{-2t} + 2\\
\quad = \quad  -2e^{-2t}\\
$$

Die Gleichung ist erfüllt.

3.  **Anfangsbedingung:** Überprüfen wir die Anfangsbedingung:

$$
y(0) = e^{-2\cdot0} + 1 = 1 + 1 = 2 = y_0
$$

Die Anfangsbedingung ist erfüllt.

**Fazit:**

Die Funktion $y(t) = y(t) = e^{-2t} + 1$ ist eine Lösung des AWP 
für $F(t, x) = 2-2x$ und $y_0 = 2$.

# Aufgabe 3

## Problemstellung

Gegeben sei die inhomogene lineare Differentialgleichung erster Ordnung:

$$
y'(t) = λy(t) + f(t), \quad t > 0
$$

wobei $\lambda \in \mathbb{R}$ eine Konstante und $f \in 
C((0, \infty))$ eine stetige Funktion auf dem offenen Intervall 
$(0, \infty)$ ist. Wir wollen (mindestens) eine Lösung dieser 
Differentialgleichung finden.

**Rechenweg:**

1.  **Ableitung von y(t):**

$$
y'(t) = α'(t)e^{λt} + αλ(t)e^{λt}
$$

2.  **Einsetzen in die Differentialgleichung:**

$$
α'(t)e^{λt} + αλ(t)e^{λt} = λ(α(t)e^{λt}) + f(t)
$$

3.  **Vereinfachen:**

$$
α'(t)e^{λt} = f(t)
$$

4.  **Lösung für $α'(t)$:**

$$
α'(t) = f(t)e^{-λt}
$$

5.  **Integration:**

    Nach dem Hauptsatz der Differential- und Integralrechnung können 
    wir $\alpha(t)$ durch Integration finden:

$$
α(t) = \int f(t)e^{-λt} dt + C
$$

wobei $C$ eine Integrationskonstante ist.

**Allgemeine Lösung:**

Setzen wir $\alpha(t)$ in den Ansatz für $y(t)$ ein, erhalten wir die
allgemeine Lösung der Differentialgleichung:

$$
y(t) = \left( \int f(t)e^{-λt} dt + C \right) e^{λt}
$$

**Bemerkung:**

Die Integrationskonstante $C$ kann durch eine Anfangsbedingung 
$y(t_0) = y_0$ bestimmt werden.

**In einfachen Worten:**

Wir haben einen Trick angewendet, um die Differentialgleichung 
zu vereinfachen. Wir haben angenommen, dass die Lösung die Form 
$y(t) = \alpha(t)e^{\lambda t}$ hat, wobei $\alpha(t)$ eine unbekannte 
Funktion ist. Durch Einsetzen in die Differentialgleichung und 
Umformen haben wir eine einfachere Gleichung für $\alpha'(t)$ 
erhalten. Diese Gleichung können wir leicht lösen, indem wir 
beide Seiten integrieren. Die resultierende Funktion $\alpha(t)$ 
setzen wir dann wieder in den Ansatz für $y(t)$ ein, um die allgemeine 
Lösung der ursprünglichen Differentialgleichung zu erhalten.



