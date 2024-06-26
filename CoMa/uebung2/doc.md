# Aufgabe 1

## Problemstellung

Wir wollen die Funktion $f(x)=sin(x)$ an den Stützstellen 
$x_0=−π, x_1 =−\frac{π}{2}, x_2=\frac{π}{2}$ und $x_3=π$ interpolieren. 

### a. Berechnung des Interpolationspolynoms (Neville-Schema)

#### Newtonsche dividierte Differenzen mit Neville-Schema

**Erklärung der Formel:**

- Basisfall: 
  - Die dividierte Differenz nullter Ordnung ist einfach der Funktionswert 
  an der entsprechenden Stützstelle:

$$
f[x_i] = f(x_i)
$$

- Rekursionsschritt: 
  - Die dividierte Differenz höherer Ordnung wird aus den dividierten 
  Differenzen niedrigerer Ordnung berechnet:

$$
f[x_i, ..., x_k] = \frac{f[x_{i+1}, ..., x_k] - f[x_i, ..., x_{k-1}]}{x_k - x_i}
$$

Diese Formel drückt die dividierte Differenz $f[x_i,...,x_k]$ als 
Differenz zweier dividierter Differenzen niedrigerer Ordnung aus,
geteilt durch die Differenz der entsprechenden Stützstellen.

**Praktische Berechnung:**

Die Berechnung der dividierten Differenzen erfolgt typischerweise in einem 
tabellarischen Schema, das oft als 
"Dreiecksschema der dividierten Differenzen" bezeichnet wird.

- Erste Spalte: Die erste Spalte enthält die Stützstellen $x_i$.
- Zweite Spalte: Die zweite Spalte enthält die Funktionswerte $f(x_i)=f[x_i]$.
- Weitere Spalten: Jede weitere Spalte wird berechnet, indem die Differenz 
der beiden Werte in der vorherigen Spalte durch die Differenz der 
entsprechenden Stützstellen geteilt wird.

**Beispiel:**

$x_i$      | $f[x_i]$    | $f[x_i,x_{i+1}]$ | $f[x_i,x_{i+1},x_{i+2}]$ | $f[x_i,...,x_{i+3}]$
------- | -------- | ------------- | ----------------------- | ------------------
$-\pi$     | 0         |                |                        |
$-\pi/2$   | -1        | $-2/\pi$            |                        |
$\pi/2$     | 1         |  $2/\pi$             | $8/(3\pi^2)$                 |
$\pi$       | 0         | $-2/\pi$           | $-8/(3\pi^2)$                      | $-8/(3\pi^3)$

Das Interpolationspolynom in Newton-Darstellung lautet:

$$
p(x) = 0 - \frac{2}{\pi}(x + \pi) + \frac{8}{3\pi^2}(x + \pi)(x + \pi/2) 
- \frac{8}{3\pi^3}(x + \pi)(x + \pi/2)(x - \pi/2)
$$

### b. Auswertung mit Horner-Schema
Das Horner-Schema ist eine effiziente Methode zur Auswertung von Polynomen.
Für unser Polynom $p(x)$ und den Wert $x=3\pi/2$ gehen wir wie folgt vor:

- Koeffizienten: 
  - Die Koeffizienten sind $a_0=0$, $a_1=-2/\pi$, $a_2=\frac{8}{(3\pi^2)}$ und 
  $a_3=-\frac{8}{3\pi^3}$.
- Initialisierung: 
  - Setze $b_3=a_3=-\frac{8}{3\pi^3}$.
- Iteration: 
  - Für $k=2,1,0$ berechne $b_k=a_k+x*b_{k+1}$ .
- Ergebnis: 
  - Der Wert $b_0$ ist das Ergebnis der Auswertung.

$$
b_2 = \frac{8}{3\pi^2} + \frac{3\pi}{2} (-\frac{8}{3\pi^3}) =
\frac{8}{3\pi^2} - \frac{12}{3\pi^2} = -\frac{4}{3\pi^2} 
$$

$$
b_1 = -\frac{2}{\pi} + \frac{3\pi}{2} (-\frac{4}{3\pi^2}) =
-\frac{2}{\pi} - \frac{2}{\pi} = -\frac{4}{\pi} 
$$


$$
b_0 = \frac{3\pi}{2} (-\frac{4}{\pi}) = -6
$$

Daher ist $p(\frac{3\pi}{2})=-6$ .

### c. Berechnung der dividierten Differenz

Wir fügen die Stützstelle $x_4=0$ hinzu und berechnen die dividierte Differenz 
$f[x_0,x_1,x_2,x_3,x_4]$:

$$
f[x_0,x_1,x_2,x_3,x_4]= \frac{f[x_1, x_2, x_3, x_4] - f[x_0, x_1, x_2, x_3]}
{x_4 - x_0}
$$

$x_i$      | $f[x_i]$    | $f[x_i,x_{i+1}]$ | $f[x_i,x_{i+1},x_{i+2}]$ | $f[x_i,...,x_{i+3}]$ | $f[x_i,...,x_{i+4}]$
------- | -------- | ------------- | ----------------------- | ------------------| ------------------
$-\pi$     | 0         |                |                        |
$-\pi/2$   | -1        | $-2/\pi$            |                        |
$\pi/2$     | 1         |  $2/\pi$             | $8/(3\pi^2)$                 |
$\pi$       | 0         | $-2/\pi$           | $-8/(3\pi^2)$                      | $-8/(3\pi^3)$
$0$       |  0        | $0$           |  $-\frac{4}{\pi^2}$                     | $-\frac{8}{3\pi^3}$ | $0$



Daher ist:

$$
f[x_0,x_1,x_2,x_3,x_4] = 0
$$

# Aufgabe 2

## Problemstellung

Sei $f:[a,b]→R$ eine unendlich oft differenzierbare Funktion, deren Ableitungen
$f^{(n)}$ alle gleichmäßig in $n$ beschränkt sind. Wenn die Intervalllänge $b−a≤1$
ist, dann konvergiert der Interpolationsfehler für jede Wahl von Stützstellen
$a=x_0 < \ldots < x_n=b$ gegen Null, wenn die Anzahl der Stützstellen gegen unendlich 
geht.

**Erklärung (in einfachen Worten):**

Stellen Sie sich vor, Sie haben eine sehr glatte Kurve (die Funktion $f(x)$),
die Sie mit einem Polynom annähern möchten. Dieses Polynom soll die Kurve an
bestimmten Punkten (den Stützstellen) genau treffen. Der Interpolationsfehler 
ist der Unterschied zwischen der ursprünglichen Kurve und dem approximierenden 
Polynom.

Der Satz besagt, dass Sie die Kurve beliebig genau annähern können, indem Sie
einfach genügend Stützstellen verwenden. Das gilt allerdings nur, wenn die 
Kurve bestimmte Eigenschaften hat:

- Unendlich oft differenzierbar: 
  - Die Kurve muss sehr glatt sein, ohne Ecken oder Knicke.

- Gleichmäßig beschränkte Ableitungen: 
  - Die Steigung der Kurve und die Änderungsraten der Steigung (und so weiter)
dürfen nicht beliebig groß werden. 

- Kurze Intervalllänge: 
  - Das Intervall, auf dem Sie die Kurve approximieren, darf nicht zu lang sein
(maximal Länge 1).

**Erklärung für Laien:**

Stellen Sie sich vor, Sie versuchen, eine sanfte Hügellandschaft mit 
Legosteinen nachzubauen. Je mehr Legosteine Sie verwenden, desto genauer können 
Sie die Landschaft nachbilden. Wenn die Landschaft jedoch zu steil oder 
zerklüftet ist, werden Sie selbst mit vielen Legosteinen keine perfekte 
Nachbildung erreichen.

Der Satz sagt uns, dass wir eine sanfte Hügellandschaft (die Funktion)
perfekt nachbauen können, wenn wir genügend Legosteine (Stützstellen)
verwenden. Allerdings müssen drei Bedingungen erfüllt sein:

- Die Landschaft darf keine abrupten Änderungen in der Höhe haben 
(unendlich oft differenzierbar).
- Die Steigung der Landschaft darf nicht zu steil sein und sich nicht zu 
schnell ändern (gleichmäßig beschränkte Ableitungen).
- Die Landschaft darf nicht zu weitläufig sein (kurze Intervalllänge).

**Beweis (mathematisch):**

Der Beweis basiert auf der Fehlerformel für die Polynominterpolation:

$$
|f(x) - p_n(x)|\ \leq \frac{f^{(n+1)}(\xi)}{(n+1)!} \prod_{i=0}^n |x - x_i|
$$


wobei:

- $p_n(x)$ das Interpolationspolynom vom Grad $n$ ist.

- $f^{(n+1)}(\xi)$ eine obere Schranke für $∣f^{(n+1)}(x)∣$ auf $[a,b]$ ist.
- Das Produkt über alle Stützstellen läuft.

> ***why you would use  n+1th derivative here?*** 
> 
> Taylor's Theorem and Error Bound
> 
> The foundation of this connection lies in Taylor's theorem, which states that
> any sufficiently smooth function can be approximated by a polynomial 
> (its Taylor series) with an error term involving the (n+1)-th derivative. 
> This error term provides an upper bound on how much the polynomial 
> approximation can deviate from the actual function.

Da alle Ableitungen von $f$ gleichmäßig beschränkt sind, existiert eine 
Konstante $M$, so dass $∣f^{(n+1)}(x)∣≤M$ für alle $n$ und alle $x∈[a,b]$.
Daher können wir $M_{n+1}=M$ in der Fehlerformel verwenden.

Nun betrachten wir den Produktterm. Da $b−a≤1$, gilt:

$$
\prod_{i=0}^n |x - x_i| \leq (b - a)^{n+1} \leq 1
$$

für alle $x∈[a,b]$.

Setzen wir diese Schranken in die Fehlerformel ein, erhalten wir:

$$
|f(x) - p_n(x)| \leq \frac{M}{(n+1)!}
$$

Wenn $n→∞$ geht, geht die rechte Seite dieser Ungleichung gegen Null, da die 
Fakultät schneller wächst als jede Exponentialfunktion. 
Daher konvergiert der Interpolationsfehler gegen Null, wenn die Anzahl der 
Stützstellen gegen unendlich geht.

# Aufgabe 3

## Problemstellung
Wir haben eine Funktion f(x), von der wir nur drei Werte kennen:

$$
f(0)=0
$$

$$
f(1)=0
$$

$$
f(1+ϵ)=1
$$

Wir möchten diese Funktion durch ein quadratisches Polynom approximieren,
das diese drei Punkte genau trifft. Um das zu erreichen, verwenden wir 
zwei Methoden: die Lagrange-Interpolation und die Newton-Interpolation.

### Lagrange-Interpolation

$$
L_1(x) = \frac{(x - 1)(x - (1 + \epsilon))}{(0 - 1)(0 - (1 + \epsilon))} =
\frac{x^2 - (2 + \epsilon)x + (1 + \epsilon)}{1 + \epsilon}
$$

$$
L_2(x) = \frac{(x - 0)(x - (1 + \epsilon))}{(1 - 0)(1 - (1 + \epsilon))} =
\frac{x^2 - (1 + \epsilon)x}{-\epsilon}
$$

$$
L_3(x) = \frac{(x - 0)(x - 1)}{((1 + \epsilon) - 0)((1 + \epsilon) - 1)} =
\frac{x^2 - x}{\epsilon(1 + \epsilon)}
$$

Das entsprechende Polynom hat die Form:

$$
p(x) =f(x_1)L_1(x) + f(x_2)L_2(x) + f(x_3)L_3(x) = \\
0 \cdot\frac{x^2 - x}{\epsilon(1 + \epsilon)} + 
0 \cdot\frac{x^2 - (1 + \epsilon)x}{-\epsilon} + 
1\cdot\frac{x^2 - x}{\epsilon(1 + \epsilon)} = \\
\frac{x^2 - x}{\epsilon(1 + \epsilon)}
$$

$$
p_L(x) = \frac{1}{\epsilon(1+\epsilon)}x^2 - \frac{1}{\epsilon(1+\epsilon)}x 
+ 0
$$

### Newton-Interpolation

$$
f[x_i,\ldots,x_k] = \frac{f[x_{i+1},\ldots,x_k]-f[x_i,\ldots,x_{k-1}]}
{x_k - x_i} 
$$
