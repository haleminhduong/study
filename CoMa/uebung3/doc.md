## Prerequisites

### Ausgangsaktivierungsfunktion

Eine Ausgangsaktivierungsfunktion, auch Output Activation Function 
genannt, ist eine spezielle Funktion, die auf die Ausgabe der 
letzten Schicht eines neuronalen Netzwerks angewendet wird. Sie 
dient dazu, die Ausgabe des Netzwerks in ein Format zu bringen, 
das für die jeweilige Aufgabe geeignet ist.

Funktionen und Anwendung:

- Identität (id): Die Identitätsfunktion gibt den Eingabewert unverändert 
zurück. Sie wird häufig verwendet, wenn das Netzwerk reelle Zahlen 
vorhersagen soll, wie z.B. bei Regressionsproblemen.

- Sigmoid: Die Sigmoidfunktion quetscht die Ausgabe des Netzwerks 
in den Bereich zwischen 0 und 1. Sie wird oft bei binären Klassifikationsproblemen 
verwendet, bei denen die Ausgabe als Wahrscheinlichkeit interpretiert wird.

- Softmax: Die Softmax-Funktion normalisiert die Ausgabe des Netzwerks 
so, dass die Summe aller Ausgaben 1 ergibt. Sie wird bei Multi-Klassen-Klassifikationsproblemen 
verwendet, um Wahrscheinlichkeiten für jede Klasse zu berechnen.

- ReLU (Rectified Linear Unit): Die ReLU-Funktion setzt negative 
Werte auf Null und lässt positive Werte unverändert. Sie wird 
häufig in den versteckten Schichten von neuronalen Netzwerken 
verwendet, aber in der Regel nicht als Ausgangsaktivierungsfunktion.

Wahl der Ausgangsaktivierungsfunktion:

Die Wahl der richtigen Ausgangsaktivierungsfunktion hängt von 
der spezifischen Aufgabe ab, die das neuronale Netzwerk lösen soll:

- Regression: Identität
- Binäre Klassifikation: Sigmoid
- Multi-Klassen-Klassifikation: Softmax

In einigen Fällen kann es sinnvoll sein, andere Aktivierungsfunktionen 
auszuprobieren, um zu sehen, ob sie bessere Ergebnisse liefern.

Beispiel:

Angenommen, wir haben ein neuronales Netzwerk, das den Preis 
eines Hauses vorhersagen soll. Da der Preis eine reelle Zahl 
ist, wäre die Identitätsfunktion eine geeignete Ausgangsaktivierungsfunktion.

### Versteckte Schichten

In einem neuronalen Netzwerk (FNN) bezieht sich der Begriff "versteckte 
Schicht" auf eine oder mehrere Schichten von Neuronen, die zwischen 
der Eingabeschicht und der Ausgabeschicht liegen. Diese Schichten 
sind "versteckt", weil sie nicht direkt mit der Außenwelt interagieren, 
sondern nur Informationen von anderen Schichten innerhalb des 
Netzwerks empfangen und verarbeiten.

Funktionsweise:

- Empfangen von Eingaben: Die Neuronen in einer versteckten Schicht 
empfangen Eingaben von den Neuronen der vorherigen Schicht (entweder 
der Eingabeschicht oder einer anderen versteckten Schicht).
- Gewichtete Summierung: Jede Eingabe wird mit einem Gewicht 
multipliziert, und alle gewichteten Eingaben werden zusammen 
mit einem Bias-Term aufsummiert.
- Aktivierungsfunktion: Die Summe wird durch eine Aktivierungsfunktion 
geleitet, die die Ausgabe des Neurons bestimmt. Diese Aktivierungsfunktion 
führt eine nichtlineare Transformation durch, die es dem Netzwerk 
ermöglicht, komplexe Beziehungen in den Daten zu lernen.
- Weitergabe der Ausgabe: Die Ausgabe des Neurons wird an die 
Neuronen der nächsten Schicht weitergeleitet.

Bedeutung:

Die versteckten Schichten sind entscheidend für die Fähigkeit 
eines neuronalen Netzwerks, komplexe Muster und Beziehungen in 
den Daten zu erkennen. Durch die Kombination mehrerer versteckter 
Schichten mit nichtlinearen Aktivierungsfunktionen können tiefe 
neuronale Netzwerke (DNNs) sehr komplexe Funktionen approximieren.

Anzahl der versteckten Schichten:

Die Anzahl der versteckten Schichten in einem neuronalen Netzwerk 
kann variieren. Ein Netzwerk mit einer einzigen versteckten Schicht 
wird als "flaches" Netzwerk bezeichnet, während ein Netzwerk 
mit mehreren versteckten Schichten als "tiefes" Netzwerk bezeichnet 
wird. Tiefe Netzwerke sind in der Regel leistungsfähiger als 
flache Netzwerke, aber sie erfordern auch mehr Trainingsdaten 
und Rechenleistung.

```
Eingabeschicht: [x] -> Versteckte Schicht -> Ausgabeschicht
```

# Aufgabe 1

## Problemstellung

Wir wollen ein Feedforward neuronales Netzwerk (FNN) konstruieren, das die 
Identitätsfunktion `id(x) = x` abbildet.
Das Netzwerk soll zwei Schichten haben, die ReLU-Aktivierungsfunktion 
verwenden und die Ausgangsaktivierungsfunktion soll die Identität sein.

## Lösung

### Neuronales Netwerk

Ein neuronales Netzwerk mit zwei Schichten und ReLU-Aktivierungsfunktion hat 
die folgende Form:

$$
h(x) = W_2 \cdot σ(W_1 \cdot x + b_1) + b_2
$$

wobei:

*   $W_1$ und $W_2$ die Gewichtsmatrizen der ersten und zweiten Schicht sind
*   $b_1$ und $b_2$ die Biasvektoren der ersten und zweiten Schicht sind
*   $\sigma(x) = \max(0, x)$ die ReLU-Aktivierungsfunktion ist

Da wir die Identitätsfunktion abbilden wollen, muss gelten:

$$
h(x) = x
$$

Eine $max\{0, x\}$ liefert $x$ bei $x\geq0$ und $0$ bei $x<0$

Eine $max\{0,-x\}$ liefert $x$ bei $x<0$ und $0$ bei $x \geq 0$. Um 
$-x$ zu bekommen verwenden wir $-max\{0,-x\}$.

Mit

$$
h(x) = max\{0,x\} - max\{0,-x\}
$$

entspricht $h(x)$ der $id(x)$.

Um dies zu erreichen, können wir die folgenden Gewichte und Biases wählen:

$$
W_1 = \begin{pmatrix} 1 \\ -1 \end{pmatrix}
$$

$$
b_1 = 0
$$

$$
W_2 = \begin{pmatrix} 1 & -1 \end{pmatrix}
$$

$$
b_2 = 0
$$

Setzen wir diese Werte in die Netzwerkgleichung ein, erhalten wir:

$$
h(x) =\begin{pmatrix} 1 & -1 \end{pmatrix}\sigma
(\begin{pmatrix} 1 \\ -1 \end{pmatrix}x + 0) + 0=\\ 
\begin{pmatrix} 1 & -1 \end{pmatrix}
\sigma(\begin{pmatrix} x \\ -x \end{pmatrix})=\\
\begin{pmatrix} 1 & -1 \end{pmatrix}
(\begin{pmatrix} max\{0,x\} \\ max\{0,-x\} \end{pmatrix})=\\
 max\{0,x\} - max\{0,-x\}
$$

Da wir die Ausgangsaktivierungsfunktion $\rho = id$ gewählt haben, gilt:

$$
h(x) = id(x) =  x
$$



# Aufgabe 2

## Problemstellung

Wir betrachten zwei neuronale Netzwerke (FNNs) $h$ und $\tilde{h}$, 
die beide von $\mathbb{R}$ nach $\mathbb{R}$ abbilden. Beide 
Netzwerke haben zwei Schichten mit der gleichen Anzahl von Neuronen 
in der versteckten Schicht und die Identitätsfunktion als Ausgangsaktivierungsfunktion. 
Die Aktivierungsfunktionen in den versteckten Schichten sind 
jedoch unterschiedlich:

*   $h$ verwendet die Sigmoid-Funktion:  $\sigma(x) = \frac{1}{1 + e^{-x}}$
*   $\tilde{h}$ verwendet die Tangens Hyperbolicus-Funktion: $\tilde{\sigma}(x) 
= \frac{e^x - e^{-x}}{e^x + e^{-x}}$

 a. Beweisen Sie, dass $\tilde{\sigma}(x) = 1 - 2\sigma(-2x)$ für alle $x \in \mathbb{R}$ gilt.

 b. Zeigen Sie, dass für beliebige Gewichte und Biasvektoren $(\tilde{W}_1, \tilde{b}_1, \tilde{W}_2, \tilde{b}_2)$ von $\tilde{h}$ entsprechende Gewichte und Biasvektoren $(W_1, b_1, W_2, b_2)$ von $h$ existieren, sodass $h = \tilde{h}$ gilt.

### a. Beweis der Beziehung zwischen den Aktivierungsfunktionen

$$
\tilde{\sigma}(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}
=\\ \frac{e^x + e^{-x} - 2e^{-x}}{e^x + e^{-x}}
=\\ 1 - \frac{2e^{-x}}{e^x + e^{-x}}
=\\ 1 - \frac{2}{e^{2x} + 1}
=\\ 1 - 2 \cdot \frac{1}{1 + e^{-(-2x)}}
=\\ 1 - 2\sigma(-2x)
$$

### b. Existenz entsprechender Gewichte und Biases:

Seien $(\tilde{W}_1, \tilde{b}_1, \tilde{W}_2, \tilde{b}_2)$ 
die Gewichte und Biases von $\tilde{h}$. Wir definieren die Gewichte 
und Biases von $h$ wie folgt:

$$
W_1 = -2\tilde{W}_1
$$

$$
b_1 = -2\tilde{b}_1
$$

$$
W_2 = -2\tilde{W}_2
$$

$$
b_2 = \tilde{b}_2 + \tilde{W}_2 
$$

Dann gilt für alle $x \in \mathbb{R}$:

$$
\tilde{h}(x) = \tilde{W}_2 \cdot \tilde{\sigma}(\tilde{W}_1 + \tilde{b}_1) +
\tilde{b}_2 =\\
\tilde{W}_2 (1 - 2\sigma(-2(\tilde{W}_1 + \tilde{b}_1))) + \tilde{b}_2 =\\
\tilde{W}_2 - 2\tilde{W}_2 \cdot \sigma(-2\tilde{W}_1 -2\tilde{b}_1) +
\tilde{b}_2 =\\
-2\tilde{W}_2 \cdot \sigma(-2\tilde{W}_1 -2\tilde{b}_1) + \tilde{b}_2 +
\tilde{W}_2 =\\
W_2 \cdot \sigma(W_1 + b_1) + b_2 = h(x)
$$

# Aufgabe 3

Für den Fall, dass du nur die Stützstellen $x_0$, $x_1$ und $x_2$ 
betrachtest, also $n=2,$ wären die Berechnungen wie folgt:

- Äquidistante Stützstellen:
  - Die äquidistanten Stützstellen im Intervall [−5,5] für n=2 sind:

$$
x_0 = a = -5
$$

$$
x_1 = a + \frac{b-a}{n} = -5 + \frac{5 - (-5)}{2} = 0
$$

$$
x_2 = b = 5
$$

- Diskrete Maximumsnorm:
  - Die diskrete Maximumsnorm mit 1001 gleichverteilten Stützstellen wird berechnet durch:

$$
∥f∥_h = \max_{i \in \{0, ..., 1000\}} \left| f \left( a + i \frac{b-a}{1000} \right) \right|
$$

  In diesem Fall ist $a=−5$ und $b=5$, also:

$$
∥f∥_h = \max_{i \in \{0, ..., 1000\}} \left| f \left( -5 + i \frac{10}{1000} \right) \right|
$$

- Interpolationspolynom:
  - Das Interpolationspolynom $p_2(x)$ vom Grad 2, das die Funktion 
  $f(x)$ an den Stützstellen $x_0$ , $x_1$ und $x_2$ interpoliert, kann 
  mit verschiedenen Methoden berechnet werden (z.B. Lagrange-Interpolation 
  oder Newton-Interpolation).

- Fehlerberechnung:
  - Der Interpolationsfehler an einer Stelle x ist gegeben durch:

$$
|f(x) - p_2(x)|
$$
  Um den Fehler für alle 1001 gleichverteilten Stützstellen zu 
  berechnen, kannst du eine Schleife verwenden und den Fehler an 
  jeder Stelle berechnen. Der maximale Fehler über alle diese Stützstellen 
  ist dann eine Approximation für die diskrete Maximumsnorm des Fehlers.

Beispiel:

Angenommen, die Funktion f(x) ist gegeben durch $f(x)=x^2$. Dann 
wäre das Interpolationspolynom:

$$
p_2(x) = \frac{25}{2} x^2 - \frac{25}{2}
$$

Du kannst nun den Fehler an jeder der 1001 Stützstellen berechnen 
und den maximalen Fehler bestimmen.
