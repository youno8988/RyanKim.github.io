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

You can copy and paste the code block below directly into your GitHub `.md` file.

***

```markdown
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
A traveling wave is a disturbance that propagates without change in amplitude or shape [1]. When propagating along the $x$-axis, it depends on both time $t$ and coordinate $x$ [1, 5]:
* Propagating in the $+x$ direction: $y = f(vt - x)$
* Propagating in the $-x$ direction: $y = g(vt + x)$

> 📊 **[Graph] Traveling Wave**
> ![Traveling Wave Graph](./images/traveling_wave.png)
> *(Insert a graph of $y=f(x,t)$ showing the propagation of a traveling wave over time here.)*

### 1.2 Harmonic Waves
The principle of a point on a string undergoing transverse simple harmonic motion is mathematically identical to a restoring force in a spring [6].
* **Restoring Force**: $F_{total} = -ky$
* **Newton's Second Law**: $m\ddot{y} = -ky \quad \Rightarrow \quad \ddot{y} + \frac{k}{m}y = 0$ (Second-order differential equation)

The solution for the displacement $y(t)$ is [6, 7]:
$$ y(t) = A\cos\left(\sqrt{\frac{k}{m}}t\right) $$
* This shows that the function's second derivative is proportional to the negative of itself, demonstrating that natural vibrational patterns perfectly match the graphs of trigonometric functions.

---

## 2. Wave Equation & Standing Waves

### 2.1 Amplitude and Standing Waves
A standing wave is formed by the superposition of an incident wave propagating in the $+x$ direction and a reflected wave propagating in the $-x$ direction [8]:
$$ y(x,t) = B\sin\left(\frac{2\pi}{\lambda}x\right)\cos(\omega t) $$
This expression combines the spatial amplitude $\left(B\sin(\frac{2\pi}{\lambda}x)\right)$ and the temporal amplitude $(\cos(\omega t))$, representing the interference between the right-traveling and left-traveling waves.

> 📊 **[Graph] Amplitude of a Standing Wave**
> ![Standing Wave Graph](./images/standing_wave.png)
> *(Insert a periodic graph showing the relationship between position $x$, wavelength $\lambda$, and amplitude $A$ here.)*

* **Propagation Constant (Wavenumber)** $k$ [7]: Specifies the number of spatial periods within $2\pi$.
  $$ k = \frac{2\pi}{\lambda}, \quad \omega = \frac{2\pi}{T}, \quad v = \frac{\omega}{k} $$

### 2.2 One-Dimensional Wave Equation
For a string under tension, applying dimensional analysis to the tension $T$ and the linear mass density $\rho$ (mass per unit length) yields the one-dimensional wave equation [9, 10]:
$$ \frac{\partial^2 y}{\partial x^2} - \frac{\rho}{T}\frac{\partial^2 y}{\partial t^2} = 0 \quad \Rightarrow \quad \frac{\partial^2 y}{\partial x^2} - \frac{1}{v^2}\frac{\partial^2 y}{\partial t^2} = 0 $$
where the phase velocity is $v = \sqrt{T/\rho}$ [9, 11].

> 📊 **[Graph] String Under Tension**
> ![Tension Graph](./images/tension.png)
> *(Insert a diagram deriving the restoring force from the tension $T$ and angle $\theta$ at the ends of a differential string element $\Delta x$.)*

---

## 3. Electromagnetic Waves & Helmholtz Equation

### 3.1 Three-Dimensional Wave Equation
The one-dimensional model generalizes to a three-dimensional wave equation for a scalar field $u(x,y,z,t)$ [12]:
$$ \frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2} + \frac{\partial^2 u}{\partial z^2} - \frac{1}{v^2}\frac{\partial^2 u}{\partial t^2} = 0 \quad \text{or} \quad \left(\nabla^2 - \frac{1}{v^2}\frac{\partial^2}{\partial t^2}\right)u = 0 $$

### 3.2 Electromagnetic Waves and Complex Notation
The harmonic temporal dependence of electromagnetic waves is often expressed in complex notation using the Euler formula [2, 13]:
$$ U(x,y,z,t) \equiv E(x,y,z)e^{-i\omega t} $$

> 📊 **[Graph] Rotation in the Complex Plane**
> ![Euler Rotation Graph](./images/euler_complex.png)
> *(Insert a unit circle diagram demonstrating that a general $e^{i\theta}$ rotates counterclockwise, while $e^{-i\omega t}$ rotates clockwise in the complex plane.)*

### 3.3 Helmholtz Equation
By substituting the complex representation of the wave into the wave equation, we obtain the Helmholtz equation, which describes the spatial properties of the electromagnetic wave [2]:
$$ \nabla^2 E(x,y,z) + k^2 E(x,y,z) = 0 \quad \text{(where } k = \frac{\omega}{v}\text{)} $$

---

## 4. Geometrical Optics & Matrix Algebra

This section treats light propagation using the geometrical optics limit. When the wavelength ($\lambda$) is negligibly small compared to the physical dimensions of the optical components, light can be modeled as geometrical rays [14, 15].

### 4.1 Fermat's Principle
When light travels through a medium with a refractive index $n$, it follows a trajectory that makes the overall optical path length a stationary value (minimum) [16]. 
$$ \delta \int_{P_1}^{P_2} n \, ds = 0 $$

### 4.2 Ray Tracing and the ABCD Matrix
The trajectory of a ray propagating through an optical system can be described using the paraxial approximation ($\sin\gamma \approx \gamma$) [3, 17, 18]. A ray is characterized by a column vector containing its height above the optical axis $x$ and its ray slope $\gamma$ [18]. 
The output parameters of the ray can be calculated by multiplying the input vector by the ray transfer matrix, known as the ABCD matrix [4]:
$$ \begin{bmatrix} x_2 \\ \gamma_2 \end{bmatrix} = \begin{bmatrix} A & B \\ C & D \end{bmatrix} \begin{bmatrix} x_1 \\ \gamma_1 \end{bmatrix} $$
* For complex lens designs, the overall system matrix is obtained by multiplying the individual refraction matrices of the curved surfaces and the propagation matrices of the distances between them [19, 20].

---
*Reference: B. D. Guenther, Modern Optics (Second Edition, Oxford University Press) & Personal Study Notes.*
```
