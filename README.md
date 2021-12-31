# Greatest-Common-Divisor-Algorithms
A Comparison between different greatest common divisor algorithms:
- Euclidian GCD.
- Extended Euclidian GCD.
- Binary GCD recursive.
- Binary GCD non-recursive.

![image](https://user-images.githubusercontent.com/56788883/147832197-75ad86df-321b-412d-98e5-1a686a9c5c95.png)

# The Intuition Behind the Binary GCD Algorithm:
- $Since,$  $d = c.gcd(a, b)$ $Given$ $that:$ $d = gcd(ac, bc)$
- $This\ intuitively\ shows\ you\ that\ if\ two\ numbers\ share\ a\ common\ divisor,\ then\ the\ difference\ between\ the\ two\ numbers\ also\ shares\ the\ same\ divisor$
```
# if u and v are even, then
    return 2*binaryGCD_rec(u >> 1, v >> 1)  # 2*gcd(u/2, v/2) (From 1)
```

- $Since,$  $gcd(a, bc) = gcd(a, b)$ $if$ $gcd(a, c) = 1$ 
- $Since$ $gcd(odd\ number, 2) = 1$
- $This\ intuitively\ shows\ you\ that\ if\ one\ of\ the\ two\ numbers\ is\ even\ then,\ we\ can\ divide\ it\ by\ 2\ and\ its\ gcd\ won't\ change$
```
# if either u or v is even, then
    return binaryGCD_rec(u >> 1, v)  # 2*gcd(u/2, v) (From 2)
    return binaryGCD_rec(u, v >> 1)  # 2*gcd(u, v/2) (From 2)
```


- $Since,$  $gcd(a, b) = gcd(a−b, b)$ $assuming$ $a > b$
- $This\ intuitively\ shows\ you\ that\ we\ can\ reduce\ numbers\ using\ their\ difference$
```
# if either u and v are odd, then
# their difference is even, then
    return binaryGCD_rec((u-v) >> 1, v)  # 2*gcd((u-v)/2, v) (From 2, 3)
# or
    return binaryGCD_rec((v-u) >> 1, u)  # 2*gcd((v-u)/2, u) (From 2, 3)
```
**Here, are the proofs of some of the used theroms and corollaries,**

# I. Prove that: if d = gcd(ac, bc), then d = c.gcd(a, b)

- $If$ $d = gcd(ac, bc)$
- $Then,$ $d|ac$ and $d|bc$
- $Then,$ $ac = dk_1$ and $bc = dk_2$
- $Then,$ $a = (d/c)k_1$ and $b = (d/c)k_2$
- $Then,$ $(d/c)|a$ and $(d/c)|b$
- $Then,$ $(d/c) = gcd(a, b)$
- $Then,$ $d = c.gcd(a, b)$

# II. Prove that: if gcd(a, c) = 1 then, gcd(a, bc) = gcd(a, b)

- $Let,$ $d = gcd(a, bc)$
- $Then,$ $d|a$ and $d|bc$
- $Assume,$ $gcd(a, c) = 1$
- $Then,$ $d$ ~~|~~ $c$ 
- $But,$ $d|bc$
- $Then,$ $d|b$
- $Then,$ $d|gcd(a, b)$
- $Assume,$ $e = gcd(a, b)$
- $By\ definition,$ $e|a$ and $e|b$
- $Then,$ $e|bc$ $Theorem$
- $Then,$ $e|d$
- $But,$ $d|e$
- $Then,$ $d = e$
- $Then,$ $gcd(a, b) = gcd(a, bc)$

# III. Prove that: gcd(a, b) = gcd(a−b, b) assuming a > b

We should prove it in the two directions:
- $Every\ common\ divisor\ of\ a\ and\ b\ is\ also\ a\ common\ divisor\ of\ a − b\ and\ b$
  - $If$ $a = dp$ and $b = dq$
  - $Then$ $a − b = d(p − q)$
- $Every\ common\ divisor\ of\ a − b\ and\ b \ is\ also\ a\ common\ divisor\ of\ a\ and\ b $
  - $If$ $a − b = dp$ and $b = dq$
  - $Then$ $a = d(p + q)$
- $Therefore,$  $gcd(a, b) = gcd(a − b, b)$
