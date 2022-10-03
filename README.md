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

  
How to run:
---
  
ulimit -s unlimited

rm -f *.o *.mod fort.*
  
ulimit -s unlimited
  
make
  
ifort -c -o opendatafile.o opendatafile.f
  
ifort -c -o tfluctq-wave.o tfluctq-wave.f
  
ifort -c -o rpq-wave.o rpq-wave.f
  
ifort -c -o prob1d.o prob1d.f90
  
ifort -c -o cdf_pd.o cdf_pd.f
  
ifort -c -o kolm2_as.o kolm2_as.f

icc -c -I/home/mehrdad/Documents/softwares/SuiteSparse-5.10.0/include umf4_f77wrapper.c


ifort -I/home/mehrdad/Documents/softwares/SuiteSparse-5.10.0/include -L/home/mehrdad/Documents/softwares/SuiteSparse-5.10.0/lib -qmkl b4step.o bc1.o ClawData.o ClawParams.o evec.o flux1.o Global1.o main.o opendatafile.o out1.o polyrecon.o qalloc1.o qinit.o reconstruct.o reconstructmd.o rpq-wave.o setaux.o setprob.o sharpclaw.o src1q-wave.o step1d.o prob1d.o cdf_pd.o kolm2_as.o tfluctq-wave.o CN.o umf4_f77wrapper.o -lumfpack -o EXE

  
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/mehrdad/Documents/softwares/SuiteSparse-5.10.0/lib/
  
export LD_LIBRARY_PATH
  
./EXE

  
Note:
---
  
You need to execute the "umf4_f77wrapper.c" on you computer by downloading the software from SuiteSparse website and install the package ("make" in the directory of the software). Then compile the file i.e. "umf4_f77wrapper.c" by: "icc -c -I/home/epfl-lhe/Desktop/suitesparse-master/include umf4_f77wrapper.c" to builde the "umf4_f77wrapper.o"






