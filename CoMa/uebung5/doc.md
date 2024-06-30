## Prerequisites

### Euler-Verfahren

Explizites Euler-Verfahren – Mathematische Formulierung

Das explizite Euler-Verfahren ist ein numerisches Verfahren zur 
näherungsweisen Lösung von Anfangswertproblemen (AWP) der Form:

$$
y'(t) = f(t, y(t)), \quad y(t_0) = y_0
$$

Die Idee besteht darin, die Lösungskurve $y(t)$ durch eine Folge von 
Geradenstücken zu approximieren. Dazu wird das Intervall $[t_0,t_n]$
in $n$ gleich große Teilintervalle der Länge $\tau$ (Schrittweite) 
unterteilt:

$$
t_k = t_0 + k\tau, \quad k = 0, 1, ..., n
$$

Die Näherungslösung $y_k$ an der Stelle $t_k$ wird dann iterativ berechnet:

$$
y_{k+1} = y_k + \tau f(t_k, y_k)
$$


# Aufgabe 1

## Problemstellung

Wir betrachten die Differentialgleichung:

$$
x'(t) = λx(t)
$$

mit $\lambda < 0$. Wir wenden das explizite Euler-Verfahren mit 
Schrittweite $\tau$ an, wobei $0 < \tau < \frac{2}{|\lambda|}$. 
Seien $x_\Delta$ und $\tilde{x}_{\Delta}$ die Näherungslösungen nach 
$n$ Schritten des Euler-Verfahrens mit Anfangswerten $x_0$ bzw. 
$\tilde{x}_{0}$. Wir wollen zeigen, dass:

$$
\|x_\Delta - \tilde{x}_{\Delta}\|_\infty = |x_0 - \tilde{x}_{0}|
$$

und interpretieren, wie sich die Stabilität des expliziten Euler-Verfahrens 
im Vergleich zur absoluten Kondition des Anfangswertproblems verhält.

## Lösung

**Beweis**:

Induktionsanfang:

$$
x_{\Delta}(0) = x_0
$$

$$
\tilde{x}_{\Delta}(0) = \tilde{x}_0
$$

$$
\|x_{\Delta}(0)-\tilde{x}_{\Delta}(0)\|_\infty = |x_0 - \tilde{x}_0|
$$

Induktionsschritt:

$$
x_{\Delta}(t_{k+1}) = x_{\Delta}(t_k)+\tau(\lambda x_k)
$$

$$
\tilde{x}_{\Delta}(t_{k+1}) = \tilde{x}_{\Delta}(t_k)+\tau(\lambda\tilde{x}_k)
$$

$$
x_{\Delta}(t_{k+1})  - \tilde{x}_{\Delta}(t_{k+1}) =\\
x_{\Delta}(t_k)+\tau(\lambda x_k) - (\tilde{x}_{\Delta}(t_k)+\tau(\lambda
\tilde{x}_k))
=\\ (1+\lambda\tau)(x_{\Delta}(t_k)-\tilde{x}_{\Delta}(t_k))
$$

$$
\|x_{\Delta}(t_{k+1}) - \tilde{x}_{\Delta}(t_{k+1})\|_\infty =
|1+\tau\lambda|\|x_0 - \tilde{x}_k\|
$$

$$
(*) 
\|x_0 - \tilde{x}_k\| = |x_0 - \tilde{x}_k|
$$

$$
\|x_{\Delta}(t_{k+1}) - \tilde{x}_{\Delta}(t_{k+1})\|_\infty =
|x_0 - \tilde{x}_k||1+ \tau\lambda|
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
\|x_{\Delta}(t_{k+1}) - \tilde{x}_{\Delta}(t_{k+1})\|_\infty =
|x_0 - \tilde{x}_k|
$$

# Aufgabe 2

## Problemstellung
Wir betrachten die Differentialgleichung:

$$
x'(t) = λx(t)
$$

mit $\lambda < 0$. Wir wenden das explizite Euler-Verfahren mit 
Schrittweite $\tau$ an, wobei $0 < \tau$. 
Seien $x_\Delta$ und $\tilde{x}_{\Delta}$ die Näherungslösungen nach 
$n$ Schritten des Euler-Verfahrens mit Anfangswerten $x_0$ bzw. 
$\tilde{x}_{0}$. Wir wollen zeigen, dass:

$$
\|x_\Delta - \tilde{x}_{\Delta}\|_\infty = |x_0 - \tilde{x}_{0}|
$$

## Lösung


**Beweis**:

Induktionsanfang:

$$
x_{\Delta}(0) = x_0
$$

$$
\tilde{x}_{\Delta}(0) = \tilde{x}_0
$$

$$
\|x_{\Delta}(0)-\tilde{x}_{\Delta}(0)\|_\infty = |x_0 - \tilde{x}_0|
$$

Induktionsschritt:

$$
x_{\Delta}(t_{k+1}) = x_{\Delta}(t_k)+\tau(\lambda x_k)
$$

$$
\tilde{x}_{\Delta}(t_{k+1}) = \tilde{x}_{\Delta}(t_k)+\tau(\lambda\tilde{x}_k)
$$

$$
x_{\Delta}(t_{k+1})  - \tilde{x}_{\Delta}(t_{k+1}) =\\
x_{\Delta}(t_k)+\tau(\lambda x_k) - (\tilde{x}_{\Delta}(t_k)+\tau(\lambda
\tilde{x}_k))
=\\ (1+\lambda\tau)(x_{\Delta}(t_k)-\tilde{x}_{\Delta}(t_k))
$$

$$
\|x_{\Delta}(t_{k+1}) - \tilde{x}_{\Delta}(t_{k+1})\|_\infty =
|1+\tau\lambda|\|x_0 - \tilde{x}_k\|
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
\|x_{\Delta}(t_{k+1}) - \tilde{x}_{\Delta}(t_{k+1})\|_\infty =
|x_0 - \tilde{x}_k|
$$
