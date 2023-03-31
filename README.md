# 1D-stochastic-deterministic-solver

1D stochastic-deterministic solver

Writen by Mehrdad Kiani Oshtorjani 

September 2022                  

LHE - EPFL              

---

This code is belongs to the paper: "Experimental and simulation studies on Bedload transport". Please cite in case of using it.

---

What is this solver?
---
This solver is for solving a coupled set of equations, namely, mass conservation, momentum conservation, Exner equation and a stochastic/deterministic equation which provide the number of moving particles:

$U_t + F(U)_x + G(U)_x = S(x,U)$

$U = [h, hv, b, yb]$

$F = [hv, (hv)^2/h+g h^2/2, \beta v b, 0]$

$G = [0, -\nu h (v)_x, -D_u (b)_x, 0]$

$S = [0, g y_b \partial y_s/\partial x +g\partial(y_b^2/2-y_s y_b)/\partial x -f v |v|/8, \lambda'-\kappa b+\xi \sqrt{2 \mu b}, \kappa V_p B^{-1} \langle b \rangle-\lambda/(1-\zeta_b)]$ 

  
