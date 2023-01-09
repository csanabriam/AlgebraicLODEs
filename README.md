# AlgebraicLODEs
<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
      <ul>
        <li><a href="#example-1">Example 1</a></li>
        <li><a href="#example-2">Example 2</a></li>
      </ul>
    <li><a href="#caveat-emptor">Caveat Emptor</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project

A package of procedures written in Maple syntax for studying linear ordinary differential equations with only algebraic solutions using Picard-Vessiot Theory. The procedures are described in the following papers.

<ul>
  <li><a href="https://doi.org/10.1016/S0022-4049(97)00018-2">M. van Hoeij, J.-A. Weil, <em>An algorithm for computing invariants of differential Galois groups</em>, Journal of Pure and Applied Algebra 117-118 (1997), p. 353-379</a></li>
  <li><a href="http://doi.org/10.1016/j.jde.2017.08.002">C. Sanabria Malagón, <em>Schwarz maps of algebraic linear ordinary differential equations</em>, Journal of Differential Equations 263 (2017), Issue 11, p. 7123-7140</a></li>
  <li><a href="https://arxiv.org/abs/1708.08555">C. Sanabria Malagón, <em>An algorithm for computing differential equations for invariant curves</em>, arXiv 1708.08555</a></li>
  <li><a href="https://doi.org/10.1016/j.jalgebra.2020.01.023">M. van der Put, C. Sanabria Malagón, J. Top, <em>Linear differential equations with finite differential Galois group</em>, Journal of Algebra 553 (2020), p. 1-25</a></li>
</ul>
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->

## Getting Started

### Prerequisites
MAPLE 2016 or newer.

### Installation
Make a copy of `AlgebraicLODEs.m` in your system and in Maple run the following commands.
  ```sh
  > read("/path_to_file/AlgebraicLODEs.m");
  > with(AlgebraicLODEs);
  ```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE EXAMPLES -->
## Usage
    
### Example 1
    
Consider the set of three generators of C[x,y]^A5 given by
  ```sh
  > J[1] := x*y*(x^10+11*x^5*y^5-y^10):
  > J[2] := -x^20-y^20+228*(x^15*y^5-x^5*y^15)-494*x^10*y^10:
  > J[3] := x^30+y^30+522*(x^25*y^5-x^5*y^25)-100005*(x^20*y^10-x^10*y^20):
  > J := [seq(J[i],i=1..3)]:
  ```
and the following three polynomials.
  ```sh
  > fI[1] := (1/2)*t^4*(t-1)^4:
  > fI[2] := 2*t^6*(t-1)^6*(t^2-t+1):
  > fI[3] := sqrt(2)*I*(t-2)*(2*t-1)*(t+1)*t^9*(t-1)^9: 
  > fI := [seq(fI[i],i=1..3)]:
  ```
We say that the arrays `J` and `fI` define a model of a curve invariant under A5 because the map C[x,y]^A5 ---> C(t), given by `J[i]` |--> `fI[i]`, for i=1,2,3, is a C-algebra homomorfism.

To get the linear ordinary differential operator in the differential algebra `[t,Dt]` that corresponds to the model, run:
  ```sh
  > L:=create_eq(2,3,J,fI,[x,y],[Dt,t]);
  ```
The output corresponds to Pépin's equation, which is an equation with Differential Galois Group A5.

### Example 2

Consider the following linear differential operator in the differential algebra `[Dx,x]`.
  ```sh
  > L := Dx^2+2/(9*x^2)+3/(16*(x-1)^2)-3/(16*x*(x-1));
  ```
To obtain candidate invariants of degree 6, run:
  ```sh
  > inv_heu(L,6,0,2,[Dx,x]);
  ```
and to obtain the invariants of degree 6, run:
  ```sh
  > invariants(L,6,0,2,[Dx,x]);
  ```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CAVEAT EMPTOR -->
## Caveat Emptor

The procedure to compute the candidate invariants and the invariants (`inv_heu` and `invariants`) only work for equations with regular singularities.
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contributing

Fork the project<br>
Create your feature branch (`git checkout -b feature/branch_name`)<br>
Commit your changes (`git commit -m 'Add a feature'`)<br>
Push to the branch (`git push origin feature/branch_name`)<br>
Open a Pull Request<br>  
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Camilo Sanabria Malagón- csanabriam@proton.me

Project Link: [https://github.com/csanabriam/AlgebraicLODEs](https://github.com/csanabriam/AlgebraicLODEs)

<p align="right">(<a href="#readme-top">back to top</a>)</p>
