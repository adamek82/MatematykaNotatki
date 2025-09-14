---
layout: default
title: "Algorytm Euklidesa: tożsamość resztowa"
permalink: /pages/gcd-euclid/
---

# Algorytm Euklidesa: tożsamość resztowa

$$
\gcd(a,b) = \gcd\big(b,\,a \bmod b\big)
$$

Poniżej porządne sformułowanie twierdzenia, lemat użyty w dowodzie oraz przykład liczbowy krok‑po‑kroku.

## Lemat (o kombinacjach liniowych)

Jeśli $d\mid a$ i $d\mid b$, to dla każdych $x,y\in\mathbb Z$ zachodzi

$$
d\mid (x a + y b).
$$

**Dowód.** Z $d\mid a$ mamy $a=du$ dla pewnego $u\in\mathbb Z$, a z $d\mid b$ mamy $b=dv$.
Wówczas $x a + y b = x(du)+y(dv)=d(xu+yv)$, czyli $d$ dzieli $x a + y b$. $\square$

## Twierdzenie (krok algorytmu Euklidesa)

Niech $a,b\in\mathbb Z$ i $b\ne 0$. Niech $q,r$ spełniają dzielenie z resztą

$$
a = q b + r,\quad 0\le r < |b|,\quad r = a\bmod b.
$$

Wtedy

$$
\gcd(a,b) = \gcd(b,r) = \gcd\big(b,\,a\bmod b\big).
$$

**Dowód.**

1. Każdy wspólny dzielnik $a$ i $b$ dzieli również $r=a-qb$ (lemat dla $x=1$, $y=-q$), więc jest wspólnym dzielnikiem $b$ i $r$.
2. Jeśli $d\mid b$ i $d\mid r$, to z $a=qb+r$ wynika $d\mid a$. Zatem każdy wspólny dzielnik $b$ i $r$ jest też wspólnym dzielnikiem $a$ i $b$.

Zbiory wspólnych dzielników są zatem identyczne, więc ich największy element (wartość $\gcd$) jest ten sam. $\square$

### Uwaga o brzegach i znakach

- Przypadek $b=0$: wyrażenie $a\bmod 0$ nie jest zdefiniowane. Standardowo przyjmujemy $\gcd(a,0)=|a|$ — to kończy algorytm.
- Znak liczb: $\gcd$ zawsze zwracamy jako liczbę nieujemną. Resztę definiujemy tak, by $0\le r<|b|$; dzięki temu twierdzenie działa także dla liczb ujemnych.
- Nie trzeba zakładać $a\ge b$. Gdy $a<b$, mamy $a\bmod b=a$, więc $\gcd(a,b)=\gcd(b,a)$.

## Przykład: $\gcd(662,\,414)$

Obliczamy kolejnymi krokami (zawsze stosując $\gcd(a,b)=\gcd(b,a\bmod b)$):

1. $\gcd(662,414)=\gcd\big(414,\,662\bmod 414\big)=\gcd(414,248)$, bo $662=1\cdot 414+248$.
2. $\gcd(414,248)=\gcd\big(248,\,414\bmod 248\big)=\gcd(248,166)$, bo $414=1\cdot 248+166$.
3. $\gcd(248,166)=\gcd\big(166,\,248\bmod 166\big)=\gcd(166,82)$, bo $248=1\cdot 166+82$.
4. $\gcd(166,82)=\gcd\big(82,\,166\bmod 82\big)=\gcd(82,2)$, bo $166=2\cdot 82+2$.
5. $\gcd(82,2)=\gcd\big(2,\,82\bmod 2\big)=\gcd(2,0)$.

Z definicji $\gcd(2,0)=2$, więc **$\gcd(662,414)=2$**.
