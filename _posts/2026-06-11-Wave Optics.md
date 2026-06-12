---
title: "[Wave Optics]"
date: 2026-02-20 11:08:00 +0900
last_modified_at: 2026-02-20 11:08:00 +0900
categories:
  - Wave Optics
tags:
  - Optic

toc: true
toc_sticky: true
---

Here is the translated README draft. I have carefully selected the exact terminology and phrasing used in B. D. Guenther's *Modern Optics* (such as "traveling wave," "harmonic temporal dependence," "paraxial approximation," and "ray transfer matrix") to ensure it perfectly aligns with standard optics literature [1-4]. 


# Modern Optics & Wave Mechanics

This repository contains study notes and summaries based on the mathematical foundations of wave theory and B. D. Guenther's *Modern Optics*.

## 📌 Table of Contents
1. [Mathematical Foundations of Waves](#1-mathematical-foundations-of-waves)
2. [Wave Equation & Standing Waves](#2-wave-equation--standing-waves)
3. [Electromagnetic Waves & Helmholtz Equation](#3-electromagnetic-waves--helmholtz-equation)
4. [Geometrical Optics & Matrix Algebra](#4-geometrical-optics--matrix-algebra)

---

## 1. Mathematical Foundations of Waves

### 1.1 Traveling Waves
A traveling wave is a disturbance that propagates without change in amplitude or shape. When propagating along the x-axis, it depends on both time t and coordinate x:
* Propagating in the +x direction: y = f(vt - x)
* Propagating in the -x direction: y = g(vt + x)

> 📊 **[Graph] Traveling Wave**
> ![Traveling Wave Graph](./images/traveling_wave.png)

### 1.2 Harmonic Waves
The principle of a point on a string undergoing transverse simple harmonic motion is mathematically identical to a restoring force in a spring.
* **Restoring Force**: F_total = -ky
* **Newton's Second Law**: m(d²y/dt²) = -ky  =>  d²y/dt² + (k/m)y = 0 (Second-order differential equation)

The solution for the displacement y(t) is:
y(t) = A cos(√(k/m) t)

* This shows that the function's second derivative is proportional to the negative of itself, demonstrating that natural vibrational patterns perfectly match the graphs of trigonometric functions.

---

## 2. Wave Equation & Standing Waves

### 2.1 Amplitude and Standing Waves
A standing wave is formed by the superposition of an incident wave propagating in the +x direction and a reflected wave propagating in the -x direction:

y(x,t) = B sin(2πx/λ) cos(ωt)

This expression combines the spatial amplitude [B sin(2πx/λ)] and the temporal amplitude [cos(ωt)], representing the interference between the right-traveling and left-traveling waves.

> **[Graph] Amplitude of a Standing Wave**

> ![alt]({{ site.url }}{{ site.baseurl }}/assets/images/waveoptics/standingwavegraph.png)

* **Propagation Constant (Wavenumber)** k: Specifies the number of spatial periods within 2π.
  k = 2π/λ,  ω = 2π/T,  v = ω/k

### 2.2 One-Dimensional Wave Equation
For a string under tension, applying dimensional analysis to the tension T and the linear mass density ρ (mass per unit length) yields the one-dimensional wave equation:

∂²y/∂x² - (ρ/T)(∂²y/∂t²) = 0   =>   ∂²y/∂x² - (1/v²)(∂²y/∂t²) = 0

where the phase velocity is v = √(T/ρ).

> 📊 **[Graph] String Under Tension**
> ![Tension Graph](./images/tension.png)

---

## 3. Electromagnetic Waves & Helmholtz Equation

### 3.1 Three-Dimensional Wave Equation
The one-dimensional model generalizes to a three-dimensional wave equation for a scalar field u(x,y,z,t):

∂²u/∂x² + ∂²u/∂y² + ∂²u/∂z² - (1/v²)(∂²u/∂t²) = 0   or   (∇² - (1/v²)(∂²/∂t²))u = 0

### 3.2 Electromagnetic Waves and Complex Notation
The harmonic temporal dependence of electromagnetic waves is often expressed in complex notation using the Euler formula:

U(x,y,z,t) ≡ E(x,y,z)e^(-iωt)

> 📊 **[Graph] Rotation in the Complex Plane**
> ![Euler Rotation Graph](./images/euler_complex.png)

### 3.3 Helmholtz Equation
By substituting the complex representation of the wave into the wave equation, we obtain the Helmholtz equation, which describes the spatial properties of the electromagnetic wave:

∇²E(x,y,z) + k²E(x,y,z) = 0   (where k = ω/v)

---

## 4. Geometrical Optics & Matrix Algebra

This section treats light propagation using the geometrical optics limit. When the wavelength (λ) is negligibly small compared to the physical dimensions of the optical components, light can be modeled as geometrical rays.

### 4.1 Fermat's Principle
When light travels through a medium with a refractive index n, it follows a trajectory that makes the overall optical path length a stationary value (minimum). 

δ ∫ n ds = 0  (from P1 to P2)

### 4.2 Ray Tracing and the ABCD Matrix
The trajectory of a ray propagating through an optical system can be described using the paraxial approximation (sin γ ≈ γ). A ray is characterized by a column vector containing its height above the optical axis x and its ray slope γ. 
The output parameters of the ray can be calculated by multiplying the input vector by the ray transfer matrix, known as the ABCD matrix:

```text
| x2 |   | A  B | | x1 |
| γ2 | = | C  D | | γ1 |
For complex lens designs, the overall system matrix is obtained by multiplying the individual refraction matrices of the curved surfaces and the propagation matrices of the distances between them.
Reference: B. D. Guenther, Modern Optics (Second Edition, Oxford University Press) & Personal Study Notes.
