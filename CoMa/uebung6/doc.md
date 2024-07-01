# Aufgabe 1

## Problemstellung

Gegeben ist das lineare Programm (LP):

$$
\text{max} \quad x1 + x2 \\
u.d.N. \quad
sx1 + t x2 ≤ 1\\
\quad x1, x2 ≥ 0
$$

Wir sollen die folgenden Mengen bestimmen und beweisen:

a) A := {(s, t) ∈ R² : (LP) hat mehr als eine optimale Lösung}

b) B := {(s, t) ∈ R² : (LP) hat genau eine optimale Lösung}

c) C := {(s, t) ∈ R² : (LP) hat keinen zulässigen Punkt}

d) D := {(s, t) ∈ R² : (LP) ist unbeschränkt}

Außerdem sollen wir für jeden Fall (falls möglich) ein Beispiel skizzieren.

**Lösung:**

**a) Menge A:**

*   **Bedingung:** Das LP hat mehr als eine optimale Lösung, wenn die Zielfunktion parallel zu einer aktiven Nebenbedingung verläuft. Dies ist der Fall, wenn $s = t$.
*   **Beweis:** Sei $s = t$. Dann ist die Nebenbedingung $sx_1 + tx_2 \le 1$ äquivalent zu $x_1 + x_2 \le \frac{1}{s}$. Die Zielfunktion $x_1 + x_2$ kann diesen Wert erreichen, und jeder Punkt auf der Geraden $x_1 + x_2 = \frac{1}{s}$ ist eine optimale Lösung.
*   **Beispiel:** Für $s = t = 1$ ist die Nebenbedingung $x_1 + x_2 \le 1$. Die Zielfunktion ist parallel zu dieser Geraden, und alle Punkte auf der Geraden sind optimale Lösungen.


**b) Menge B:**

*   **Bedingung:** Das LP hat genau eine optimale Lösung, wenn die Zielfunktion nicht parallel zu einer aktiven Nebenbedingung verläuft. Dies ist der Fall, wenn $s \neq t$.
*   **Beweis:** Sei $s \neq t$. Dann schneidet die Zielfunktion die Nebenbedingung $sx_1 + tx_2 \le 1$ in einem eindeutigen Punkt, der die optimale Lösung darstellt.
*   **Beispiel:** Für $s = 2$ und $t = 1$ ist die Nebenbedingung $2x_1 + x_2 \le 1$. Die Zielfunktion schneidet diese Gerade im Punkt (0, 1), der die eindeutige optimale Lösung ist.


**c) Menge C:**

*   **Bedingung:** Das LP hat keinen zulässigen Punkt, wenn die Nebenbedingung nicht erfüllbar ist. Dies ist der Fall, wenn $s < 0$ oder $t < 0$.
*   **Beweis:** Wenn $s < 0$ oder $t < 0$, dann gibt es keine nicht-negativen Werte für $x_1$ und $x_2$, die die Nebenbedingung erfüllen.
*   **Beispiel:** Für $s = -1$ und $t = 1$ ist die Nebenbedingung $-x_1 + x_2 \le 1$. Es gibt keine nicht-negativen Werte für $x_1$ und $x_2$, die diese Ungleichung erfüllen.


**d) Menge D:**

*   **Bedingung:** Das LP ist unbeschränkt, wenn die Zielfunktion in Richtung der zulässigen Menge beliebig groß werden kann. Dies ist der Fall, wenn $s \le 0$ und $t \le 0$, aber nicht beides gleichzeitig Null ist.
*   **Beweis:** Wenn $s \le 0$ und $t \le 0$, dann können wir $x_1$ oder $x_2$ beliebig groß machen, ohne die Nebenbedingung zu verletzen. Da die Zielfunktion $x_1 + x_2$ ist, kann sie auch beliebig groß werden.
*   **Beispiel:** Für $s = -1$ und $t = 0$ ist die Nebenbedingung $-x_1 \le 1$. Wir können $x_1$ beliebig klein (negativ) machen, und die Zielfunktion wird beliebig groß.

