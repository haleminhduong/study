## Prerequisite

### Determinant

To calculate a determinant there's a handy mnemonic called the Rule of Sarrus

$$
\begin{vmatrix}
a & b & c \\
d & e & f \\
g & h & i 
\end{vmatrix}
$$

Downward diagonals
$$
a \cdot e \cdot i + b \cdot f \cdot g + c \cdot d \cdot h
$$

Upward diagonals

$$
c \cdot e \cdot g + a \cdot f \cdot h + b \cdot d \cdot i
$$


$$
\det(M) = (a \cdot e \cdot i + b \cdot f \cdot g + c \cdot d \cdot h) - 
(c \cdot e \cdot g + a \cdot f \cdot h + b \cdot d \cdot i)
$$

### Adjugate

The adjugate of a matrix is the transpose of its cofactor matrix. The cofactor
$C_ij$ of an element $a_ij$ in a matrix $A$ is the determinant of the submatrix
obtained by deleting the $i$-th row and $j$-th column, multiplied by
$(−1)^{i+j}$:

$$
C_{ij} = (-1)^{i+j} \det(M_{ij})
$$

$$
\text{adj}(M) = {C_{ij}}^T
$$

# Aufgabe 1
## Problemstellung

Wir haben eine Funktion f(x), von der wir nur drei Werte kennen:

$$f(0)=0$$
$$f(1)=0$$
$$f(1+ϵ)=1$$
Wir möchten diese Funktion durch ein quadratisches Polynom $p(x)$ annähern, das
diese drei Punkte genau trifft. Um das zu erreichen, verwenden wir die 
Lagrange-Interpolation.

### a. Aufstellen von Matrix und Vektor

Die Matrix $M$ und der Vektor $b$ für das Gleichungssystem $Ma=b$ ergeben sich 
aus den Stützstellen und Funktionswerten:

$$
M = \begin{pmatrix}
1 & 0 & 0 \\
1 & 1 & 1 \\
1 & 1 + \epsilon & (1 + \epsilon)^2
\end{pmatrix}, \quad
b = \begin{pmatrix}
0 \\
0 \\
1
\end{pmatrix}
$$

### b. Berechnung des Koeffizientenvektors

Um den Koeffizientenvektor $a$ zu finden, müssen wir das Gleichungssystem
$Ma=b$ lösen. Das können wir machen, indem wir die Inverse von M berechnen
und mit b multiplizieren:

$$
a = M^{-1} b
$$

Die Inverse von M lässt sich mit der Formel 

$$
M^{−1} = \frac{1}{det(M)}adj(M) 
$$

berechnen. 

$$
\det(M) = 1 \cdot \begin{vmatrix} 1 & 1 \\ 1+\epsilon & (1+\epsilon)^2
\end{vmatrix} - 0 + 0 = (1+\epsilon)^2 - (1+\epsilon) = \epsilon(1+\epsilon)
$$

Als nächstes berechnen wir die Adjunkte von M. Dazu bestimmen wir die 
Kofaktorenmatrix und transponieren diese:

$$
\text{cof}(M) = \begin{pmatrix}
(1+\epsilon)^2 - (1+\epsilon) & -(1+\epsilon) + 1 & 1 - 1 \\
-(1+\epsilon) & (1+\epsilon)^2 & -1 \\
1 & -1 & \epsilon
\end{pmatrix} = \begin{pmatrix}
\epsilon(1+\epsilon) & -\epsilon & 0 \\
-(1+\epsilon) & (1+\epsilon)^2 & -1 \\
1 & -1 & \epsilon
\end{pmatrix}
$$

$$
M^{-1} = \frac{1}{\det(M)} \text{adj}(M) = \frac{1}{\epsilon(1+\epsilon)} \begin{pmatrix}
\epsilon(1+\epsilon) & -(1+\epsilon) & 1 \\
-\epsilon & (1+\epsilon)^2 & -1 \\
0 & -1 & \epsilon
\end{pmatrix} = 
\begin{pmatrix}
1 & -\frac{1}{\epsilon} & \frac{1}{\epsilon(1+\epsilon)} \\
-\frac{1}{1+\epsilon} & \frac{1+\epsilon}{\epsilon} & -\frac{1}{\epsilon(1+\epsilon)} \\
0 & -\frac{1}{\epsilon} & \frac{1}{1+\epsilon}
\end{pmatrix}
$$

$$
a = M^{-1} b = \begin{pmatrix}
1 & -\frac{1}{\epsilon} & \frac{1}{\epsilon(1+\epsilon)} \\
-\frac{1}{1+\epsilon} & \frac{1+\epsilon}{\epsilon} & -\frac{1}{\epsilon(1+\epsilon)} \\
0 & -\frac{1}{\epsilon} & \frac{1}{1+\epsilon}
\end{pmatrix} \begin{pmatrix}
0 \\
0 \\
1
\end{pmatrix} = \begin{pmatrix}
0 \\
-\frac{1}{\epsilon} \\
\frac{1}{\epsilon}
\end{pmatrix}
$$

$$
a = \begin{pmatrix}
0 \\
-\frac{1}{\epsilon} \\
\frac{1}{\epsilon}
\end{pmatrix}
$$

### c. Auswerten des Polynoms
Das Interpolationspolynom ist also:

$$
p(x) = -\frac{1}{\epsilon} x + \frac{1}{\epsilon} x^2
$$

Um $f(x)$ an der Stelle $x=\frac{1}{2}$ zu approximieren, setzen wir diesen Wert
in das Polynom ein:

$$
p\left(\frac{1}{2}\right) = -\frac{1}{2\epsilon} + \frac{1}{4\epsilon} =
-\frac{1}{4\epsilon}
$$

### d. Konditionszahl der Matrix

Die Konditionszahl $κ_∞(M)$ gibt an, wie empfindlich das Gleichungssystem auf
kleine Änderungen in den Eingabedaten reagiert. Wir berechnen sie mithilfe der 
Maximumsnorm:

$$
\kappa_\infty(M) = \|M\|_\infty \|M^{-1}\|_\infty
$$

$$
\|M\|_\infty = \max_{1 \le i \le n} \sum_{j=1}^n |m_{ij}|
$$

In unserem Fall:

$$
M = \begin{pmatrix}
1 & 0 & 0 \\
1 & 1 & 1 \\
1 & 1 + \epsilon & (1 + \epsilon)^2
\end{pmatrix}
$$

Zeile 1:

$$
|1| + |0| + |0| = 1
$$

Zeile 2:

$$
|1| + |1| + |1| = 3
$$

Zeile 3:

$$
|1| + |1 + \epsilon| + |{(1 + \epsilon)}^2| = 1 + 1 + \epsilon + 1 + 2\epsilon
+ \epsilon^2 = 3 + 3\epsilon + \epsilon^2
$$

da $\epsilon^2$ sehr klein ist, ist nur $3 + 3\epsilon$ verblieben

$$
\|M\|_\infty = \max \{1, 3, 3+3\epsilon\} = 3+3\epsilon
$$

$$
|M^{-1}| =
\begin{pmatrix}
1 & -\frac{1}{\epsilon} & \frac{1}{\epsilon(1+\epsilon)} \\
-\frac{1}{1+\epsilon} & \frac{1+\epsilon}{\epsilon} & -\frac{1}{\epsilon(1+\epsilon)} \\
0 & -\frac{1}{\epsilon} & \frac{1}{1+\epsilon}
\end{pmatrix}
$$

Zeile 1:

$$
|1| + |-\frac{1}{\epsilon}| + |\frac{1}{\epsilon(1+\epsilon)}| = 1 +
\frac{1}{\epsilon} + \frac{1}{\epsilon(1+\epsilon)}
$$

Zeile 2:

$$
|-\frac{1}{1+\epsilon}| + |\frac{1+\epsilon}{\epsilon}| + 
|-\frac{1}{\epsilon(1+\epsilon)}| =
\frac{1}{1+\epsilon} + \frac{1+\epsilon}{\epsilon} + 
\frac{1}{\epsilon(1+\epsilon)}
$$

Zeile 3:

$$
0 + |-\frac{1}{\epsilon}| + |\frac{1}{1+\epsilon}| =
\frac{1}{\epsilon} + \frac{1}{1+\epsilon} 
$$

Zeile 1 < Zeile 2 wegen $0 <\frac{1}{1+\epsilon}$

Zeile 3 < Zeile 2 wegen 

$$
\frac{1}{\epsilon} + \frac{1}{1+\epsilon} <
\frac{1}{1+\epsilon} + \frac{1+\epsilon}{\epsilon}   
$$

$$
\|M^{-1}\|_\infty = 
\frac{1}{1+\epsilon} + \frac{1+\epsilon}{\epsilon} + 
\frac{1}{\epsilon(1+\epsilon)} =
\frac{\epsilon + (1+\epsilon)^2 + 1}{\epsilon(1+\epsilon)} = 
\frac{(1 + 1 + \epsilon)(1 + \epsilon)}{\epsilon(1 + \epsilon)} =
\frac{(2 + \epsilon)(1 + \epsilon)}{\epsilon(1 + \epsilon)} =
\frac{2 + \epsilon}{\epsilon}
$$

$$
\kappa_\infty(M) = \frac{(2+\epsilon)(3+3\epsilon)}{\epsilon}
$$

Um die Konditionszahl $(\kappa_\infty(M))$ zu berechnen, substituieren wir die gegebene Formel und vereinfachen sie:

$$
\kappa_\infty(M) = \frac{(2+\epsilon)(3+3\epsilon)}{\epsilon}
$$

Wir multiplizieren die Terme im Zähler:

$$
(2 + \epsilon)(3 + 3\epsilon) = 2 \cdot 3 + 2 \cdot 3\epsilon + \epsilon \cdot 3 + \epsilon \cdot 3\epsilon = 6 + 6\epsilon + 3\epsilon + 3\epsilon^2
$$

Das vereinfacht sich zu:

$$
6 + 9\epsilon + 3\epsilon^2
$$

Jetzt setzen wir dies zurück in die ursprüngliche Formel ein:

$$
\kappa_\infty(M) = \frac{6 + 9\epsilon + 3\epsilon^2}{\epsilon}
$$

Teilen wir jeden Term im Zähler durch (\epsilon):

$$
\kappa_\infty(M) = \frac{6}{\epsilon} + \frac{9\epsilon}{\epsilon} + \frac{3\epsilon^2}{\epsilon} = \frac{6}{\epsilon} + 9 + 3\epsilon
$$

Somit ist die Konditionszahl:

$$
\kappa_\infty(M) = \frac{6}{\epsilon} + 9 + 3\epsilon
$$

Die Konditionszahl $(\kappa_\infty(M))$ ist ein Maß für die Sensitivität der Lösung eines linearen Systems gegenüber Änderungen oder Störungen in den Eingangsdaten oder im System selbst. Im Kontext der Berechnung dieser spezifischen Konditionszahl:

$$
\kappa_\infty(M) = \frac{6}{\epsilon} + 9 + 3\epsilon
$$

und im Grenzfall $(\epsilon\to0):$

$$
\kappa_\infty(M) \approx \frac{6}{\epsilon}
$$

können wir einige wichtige Eigenschaften und Schlussfolgerungen ableiten:

- **Hohe Sensitivität für kleine $(\epsilon)$**: Da $(\kappa_\infty(M))$ 
für $(\epsilon\to0)$ gegen $(\infty)$ divergiert, zeigt dies, dass das
System extrem empfindlich auf kleine Störungen oder Änderungen in den 
Eingabedaten reagiert. Selbst eine geringe Veränderung in den
Eingangsdaten kann zu einer großen Veränderung in der Lösung führen.

- **Stabilität und Numerische Genauigkeit**: Eine 
hohe Konditionszahl deutet auf ein schlecht konditioniertes Problem hin. 
Solche Probleme sind numerisch instabil und erfordern besondere Vorsicht 
bei der Berechnung der Lösungen. Es besteht ein höheres Risiko von 
Rundungsfehlern und Ungenauigkeiten bei der numerischen Lösung.

- **Bewertung der Matrizen**: In praktischen Anwendungen bedeutet 
eine sehr hohe Konditionszahl, dass die Matrix $(M)$ nahe an der 
Singularität ist, d.h., sie ist nahezu nicht invertierbar. In 
solchen Fällen sind spezielle numerische Techniken erforderlich, um 
zuverlässige Ergebnisse zu erzielen.

Zusammengefasst:

- **Geringe $(\epsilon)$ führt zu hoher Konditionszahl**: 
Dies zeigt, dass das System sehr empfindlich und numerisch instabil ist.
- **Numerische Vorsicht geboten**: Bei der Lösung von Problemen mit 
hohen Konditionszahlen sind spezielle numerische Verfahren erforderlich, 
um genaue und stabile Lösungen zu gewährleisten.

# Aufgabe 2

## Problemstellung

Gegeben sind $n$ paarweise verschiedene Punkte $x_1,x_2,...,x_n∈R$.
Wir definieren die Matrix $M∈R^{n×n}$ durch:

$$
M_{ij} = x_i^{j-1} \quad \text{für } i, j \in \{1, ..., n\}
$$

Diese Matrix wird auch als Vandermonde-Matrix bezeichnet. 
Wir wollen beweisen, dass $M$ regulär ist, d.h., dass sie invertierbar ist.

## Beweis

Eine Matrix ist genau dann regulär, wenn ihre Determinante ungleich
Null ist. Wir werden zeigen, dass die Determinante der 
Vandermonde-Matrix M nicht Null sein kann, wenn die $x_i$
paarweise verschieden sind.

Die Determinante einer Vandermonde-Matrix lässt sich explizit berechnen:

$$
\det(M) = \prod_{1 \le i < j \le n} (x_j - x_i)
$$


Da die $x_i$ paarweise verschieden sind, sind alle Faktoren $(x_j−x_i)$ 
in diesem Produkt ungleich Null. Daher ist das Produkt selbst 
auch ungleich Null:

$$
\det(M) \neq 0
$$

Schlussfolgerung:

Da die Determinante der Vandermonde-Matrix $M$ ungleich Null ist, 
ist $M$ regulär (invertierbar).

Intuitive Erklärung:

Die Vandermonde-Matrix repräsentiert ein lineares Gleichungssystem,
das entsteht, wenn man ein Polynom vom Grad höchstens $n−1$ an $n$
verschiedenen Punkten interpolieren möchte. Die Regularität der 
Matrix bedeutet, dass dieses Interpolationsproblem eine eindeutige 
Lösung hat, d.h., es gibt genau ein Polynom vom Grad höchstens $n−1$,
das durch die gegebenen Punkte verläuft.
