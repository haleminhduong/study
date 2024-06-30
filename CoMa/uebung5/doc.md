## Prerequisites

### Euler-Verfahren

Explizites Euler-Verfahren – Mathematische Formulierung

Das explizite Euler-Verfahren ist ein numerisches Verfahren zur 
näherungsweisen Lösung von Anfangswertproblemen (AWP) der Form:

$$
y'(t) = f(t, y(t)), \quad y(t\_0) = y\_0
$$

Die Idee besteht darin, die Lösungskurve $y(t)$ durch eine Folge von 
Geradenstücken zu approximieren. Dazu wird das Intervall $[t\_0,t\_n]$
in $n$ gleich große Teilintervalle der Länge $\tau$ (Schrittweite) 
unterteilt:

$$
t\_k = t\_0 + k\tau, \quad k = 0, 1, ..., n
$$

Die Näherungslösung $y\_k$ an der Stelle $t\_k$ wird dann iterativ berechnet:

$$
y\_{k+1} = y\_k + \tau f(t\_k, y\_k)
$$


# Aufgabe 1

## Problemstellung

Wir betrachten die Differentialgleichung:

$$
x'(t) = λx(t)
$$

mit $\lambda < 0$. Wir wenden das explizite Euler-Verfahren mit 
Schrittweite $\tau$ an, wobei $0 < \tau < \frac{2}{|\lambda|}$. 
Seien $x\_\Delta$ und $\tilde{x}\_{\Delta}$ die Näherungslösungen nach 
$n$ Schritten des Euler-Verfahrens mit Anfangswerten $x\_0$ bzw. 
$\tilde{x}\_{0}$. Wir wollen zeigen, dass:

$$
\|x\_\Delta - \tilde{x}\_{\Delta}\|\_\infty = |x\_0 - \tilde{x}\_{0}|
$$

und interpretieren, wie sich die Stabilität des expliziten Euler-Verfahrens 
im Vergleich zur absoluten Kondition des Anfangswertproblems verhält.

## Lösung

**Beweis**:

Induktionsanfang:

$$
x\_{\Delta}(0) = x\_0
$$

$$
\tilde{x}\_{\Delta}(0) = \tilde{x}\_0
$$

$$
\|x\_{\Delta}(0)-\tilde{x}\_{\Delta}(0)\|\_\infty = |x\_0 - \tilde{x}\_0|
$$

Induktionsschritt:

$$
x\_{\Delta}(t\_{k+1}) = x\_{\Delta}(t\_k)+\tau(\lambda x\_k)
$$

$$
\tilde{x}\_{\Delta}(t\_{k+1}) = \tilde{x}\_{\Delta}(t\_k)+\tau(\lambda\tilde{x}\_k)
$$

$$
x\_{\Delta}(t\_{k+1})  - \tilde{x}\_{\Delta}(t\_{k+1}) =\\
x\_{\Delta}(t\_k)+\tau(\lambda x\_k) - (\tilde{x}\_{\Delta}(t\_k)+\tau(\lambda
\tilde{x}\_k))
=\\ (1+\lambda\tau)(x\_{\Delta}(t\_k)-\tilde{x}\_{\Delta}(t\_k))
$$

$$
\|x\_{\Delta}(t\_{k+1}) - \tilde{x}\_{\Delta}(t\_{k+1})\|\_\infty =
|1+\tau\lambda|\|x\_0 - \tilde{x}\_k\|
$$

$$
(*) 
\|x\_0 - \tilde{x}\_k\| = |x\_0 - \tilde{x}\_k|
$$

$$
\|x\_{\Delta}(t\_{k+1}) - \tilde{x}\_{\Delta}(t\_{k+1})\|\_\infty =
|x\_0 - \tilde{x}\_k||1+ \tau\lambda|
$$

$$
0<\tau<\frac{2}{|\lambda|} \\
0<\tau|\lambda|<2\\
0>-\tau|\lambda|>-2\\
1> 1-\tau|\lambda|>-1\\
(*)\lambda<0 \to |\lambda| = -\lambda\\
-1<1+\tau\lambda<1\\
0<|1+\tau\lambda|<1
$$

da dieser Term kleiner als 1 ist, anhand der Definintion von absoluter
Kondition hat er keinen Einfluss of den ganzen Term, gilt die Aussage:

$$
\|x\_{\Delta}(t\_{k+1}) - \tilde{x}\_{\Delta}(t\_{k+1})\|\_\infty =
|x\_0 - \tilde{x}\_k|
$$

# Aufgabe 2

## Problemstellung
Wir betrachten die Differentialgleichung:

$$
x'(t) = λx(t)
$$

mit $\lambda < 0$. Wir wenden das explizite Euler-Verfahren mit 
Schrittweite $\tau$ an, wobei $0 < \tau$. 
Seien $x\_\Delta$ und $\tilde{x}\_{\Delta}$ die Näherungslösungen nach 
$n$ Schritten des Euler-Verfahrens mit Anfangswerten $x\_0$ bzw. 
$\tilde{x}\_{0}$. Wir wollen zeigen, dass:

$$
\|x\_\Delta - \tilde{x}\_{\Delta}\|\_\infty = |x\_0 - \tilde{x}\_{0}|
$$

## Lösung


**Beweis**:

Induktionsanfang:

$$
x\_{\Delta}(0) = x\_0
$$

$$
\tilde{x}\_{\Delta}(0) = \tilde{x}\_0
$$

$$
\|x\_{\Delta}(0)-\tilde{x}\_{\Delta}(0)\|\_\infty = |x\_0 - \tilde{x}\_0|
$$

Induktionsschritt:

$$
x\_{\Delta}(t\_{k+1}) = x\_{\Delta}(t\_k)+\tau(\lambda x\_k)
$$

$$
\tilde{x}\_{\Delta}(t\_{k+1}) = \tilde{x}\_{\Delta}(t\_k)+\tau(\lambda\tilde{x}\_k)
$$

$$
x\_{\Delta}(t\_{k+1})  - \tilde{x}\_{\Delta}(t\_{k+1}) =\\
x\_{\Delta}(t\_k)+\tau(\lambda x\_k) - (\tilde{x}\_{\Delta}(t\_k)+\tau(\lambda
\tilde{x}\_k))
=\\ (1+\lambda\tau)(x\_{\Delta}(t\_k)-\tilde{x}\_{\Delta}(t\_k))
$$

$$
\|x\_{\Delta}(t\_{k+1}) - \tilde{x}\_{\Delta}(t\_{k+1})\|\_\infty =
|1+\tau\lambda|\|x\_0 - \tilde{x}\_k\|
$$

$$
\tau > 0
$$

$$
\lambda < 0 \to |\lambda| = -\lambda
$$

$$
\tau|\lambda| > 0\\
-\tau\lambda > 0\\
\tau\lambda<0\\
1+\tau\lambda<1\\
0<|1+\tau\lambda| < 1
$$

da dieser Term kleiner als 1 ist, anhand der Definintion von absoluter
Kondition hat er keinen Einfluss of den ganzen Term, gilt die Aussage:

$$
\|x\_{\Delta}(t\_{k+1}) - \tilde{x}\_{\Delta}(t\_{k+1})\|\_\infty =
|x\_0 - \tilde{x}\_k|
$$
