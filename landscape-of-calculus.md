---
jupytext:
  cell_metadata_filter: -all
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.16.1
kernelspec:
  display_name: Wolfram Language 14
  language: Wolfram Language
  name: wolframlanguage14
---

# Landscape of Calculus

Calculus is the study of *continuous change*.
We indicate something that will change,
or vary, using a varaible such as $x$ or $y$.

Consider a real variable $y$ 
whose initial value is $1$ and later changes to $3$.
The *amount of change* in $y$ is defined to 
be the difference[^distance] between the initial and final values:

$$
\Delta y = 3 - 1 = 2.
$$

The difference in a variable $y$ is denoted by prepending
$y$ with the symbol $\Delta$, the capital D in Greek.

[^distance]: {-} The measurement of difference depends on
the type of objects $y$ being of.
For instance, the difference between two time series can
be measured by the dynamic time warping algorithms.

Measuring change is more of a defining routine as shown above.
In science and in several applications of calculus,
we concern about how one change affects another.
The relation between two variables is usually modeled through
a function:

$$
y = f(x).
$$

## Continuity 

What does it mean when we say that a change is *continuous*?
In particular, what dose it mean when we say that the change in $y$
with repect to $x$ is continous?
A change is continous if it happens gradually, 
no steep, interruption, abrupt, or some crazy stuff as illustrated below[^discont-exmp-epilog].

[^discont-exmp-epilog]: The problem location is colored grey.

`````{tab-set}
````{tab-item} Steep
```{margin}
The function $1/x^2$ goes steep as $x$ approaches $0$.
```
```{image} images/inf-discont.pdf
:width: 100%
:align: center
```
````

````{tab-item} Interruption
```{margin}
The function $\frac{\sin(x)}{x}$ looks great but has an undefind point at $x = 0$.
```
```{image} images/rm-discont.pdf
:width: 100%
:align: center
````

````{tab-item} Abrupt
```{margin}
The pieciewise function 
has a sudden change when $x$ near $0$.
```
```{image} images/jump-discont.pdf
:width: 100%
:align: center
```
````

````{tab-item} Crazy
```{margin}
The function $\sin(1/x)$ never settles down when $x$ goes to zero.
```

```{image} images/crazy-discont.pdf
:width: 100%
:align: center
````
`````

The function $y = f(x)$ is continuous at $x = a$
if

{style=lower-roman}
1. it is defined on $x=a$, and[^cont-inf-conds]
2. an infinitesimal change in $x$ around $x=a$
  results in infinitesimal change in $y$.

[^cont-inf-conds]: {-} The first condition rules out the case of interruption,
and the second rules out the cases of steep, abrupt, 
and any unsteady behaviour near the point $x=a$.

To denote infinitesimal change, subsitute the $\Delta$ with small "d".
Then we can write the defining conditions for continuity at $x = a$ as:

```{math}
:label: infsmll_cont

dy = f(a + dx) - f(a).
```

[^test-infsmll-cont]: {-} You should verify 
this definition by examine the above examples
of discontinuities at the problem points.

Early mathematicians lack the tools to provide 
rigoroness for the notion of infinitesimals.[^infsmll-rebrand]
So it is replaced by the notion of limits in modern calculus.
You can think of an infinitesimal quantity as 
a *limit appraoching $0$*.

Rewrite {eq}`infsmll_cont` using the notion of limits:

```{margin}
You might read the eqaution as a limit "equals" zero.
But notice that the notion of limits is always "approaching".
So what the equation says is that the change in $y$
is sufficiently close to zero that no one can distinguish it from zero.
```

```{math}
:label: limit_cont_1
\lim_{\Delta x \to 0} f(a + \Delta x) - f(a) = 0.
```

Further simplify the equation above:

```{math}
:label: limit_cont_2
f(a) = \lim_{\Delta x \to 0} f(a + \Delta x)
     = \lim_{x \to a} f(x). 
```

The first equality in {eq}`limit_cont_2` is deduced from {eq}`limit_cont_1`
by simple algebra.
The second equality is due to the fact that when $\Delta x$ goes to $0$,
the variable $x$ goes to its inital value $a$.

[^infsmll-rebrand]: {-} The rigorous treatment of infinitesimals
didn't succeed unitl the 1960s.


```{prf:definition} Continuity
:label: continuity

A function $f(x)$ is *continuous* at $x=a$ if

$$
f(a) = \lim_{x \to a} f(x).
$$

A *continuous funciton* is a function whose domain
is an interval, and it is continuous at every point
within its domain.
```

## Derivatives as Rates of Changes

The definition of continuity of $y = f(x)$ describes 
a qualitative relation between the change in $y$ and the change in $x$,
the $\Delta y$ should be small if $\Delta x$ is small.
The derivative of a function gives a quantative relation,
as it enables us to compute an exact quantity of $\Delta y$ when $\Delta x$ is known.  

For illustration, we consider the function $p(t) = \sqrt{t}$ 
such that $p(t_0)$ is the position of
a car moving along a straight line at time $t_0$.

A driver is concerned about the velocity $v$ we have to drive in order to 
arrive $p = 10$ at $t = 4$, starting from some time, say, $t = 1$.
It is impossible to drive at a constant velocity.
So the problem actually asks about the average velocity:

$$ 
v = \frac{\Delta p}{\Delta t} = \frac{10 - p(1)}{4 - 1} = 3.
$$


A police cares more about whether you are speeding at a moment.
A speed camera computes your speed instantly as you pass through it.
In other words, it computes your speed with a very small $\Delta t$,
and so $\Delta p$ should also be very small[^diff-cont].
So the velocity at a moment can be computed as a *rate of infinitesimal changes*:

```{math}
:label: velocity
v(t) = \frac{dp}{dt} = \lim_{\Delta t \to 0}\frac{p(t + \Delta t) - p(t)}{\Delta t}.
```

[^diff-cont]: Continuity is the necessary condition for differentiability.

It is obvious from the above equationa that calculus is involved, 
since it contains infinitesimals $dp$ and $dt$.


````{prf:definition} Derivatives
The *derivative* of a function $f(x)$ 
is the function $f'(x)$ defined as:

```{math}
:label: derivative_dfn
f'(x) = \frac{df}{dx} = \lim_{\Delta x \to 0} \frac{f(x + \Delta x) - f(x)}{\Delta x}.
```

When the derivative is evaluated at a speicifc point $x = a$,
it is called the derivative of $f$ at $x = a$, written as  $f'(a)$.
````

````{prf:example} 
Differente $p(t) = \sqrt{t}$ using {eq}`derivative_dfn`[^differentiation].

[^differentiation]: {-} The procedure to compute the derivative of a function
is called *differentiation*.

```{margin}
\
\
\
\
$a^2 - b^2 = (a+b)(a-b)$
```

$$
\begin{aligned}
v(t) = \frac{dp}{dt} 
      &= \lim_{\Delta t \to 0}\frac{\sqrt{t + \Delta t} - \sqrt{t}}{\Delta t} \\
      &= \lim_{\Delta t \to 0} \frac{\sqrt{t + \Delta t} - \sqrt{t} }{\Delta t}
       \left(
        \frac{\sqrt{t + \Delta t} + \sqrt{t}}{\sqrt{t + \Delta t} + \sqrt{t}} 
        \right) \\
      &= \lim_{\Delta t \to 0}\frac{\Delta t}{\Delta t (\sqrt{t + \Delta t} + \sqrt{t})} \\
      &= \lim_{\Delta t \to 0}\frac{1}{\sqrt{t + \Delta t} + \sqrt{t}}
       = \frac{1}{2\sqrt{t}}.
\end{aligned}
$$

Hence $v(t) = p'(t) = 1/(2 \sqrt{t})$.
````

