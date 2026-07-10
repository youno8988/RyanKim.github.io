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

> **[Graph] Traveling Wave**
> ![트래블링 웨이브 그래프]({{ site.baseurl }}/assets/images/waveoptics/travelingwavegraph.png)

### 1.2 Harmonic Waves
The principle of a point on a string undergoing transverse simple harmonic motion is mathematically identical to a restoring force in a spring.
* **Restoring Force**: F_total = -ky
* **Newton's Second Law**: m(d²y/dt²) = -ky  =>  d²y/dt² + (k/m)y = 0 (Second-order differential equation)

The solution for the displacement y(t) is:
y(t) = A cos(√(k/m) t)

* This shows that the function's second derivative is proportional to the negative of itself, demonstrating that natural vibrational patterns perfectly match the graphs of trigonometric functions.

---
<div style="border: 1px solid #ddd; border-radius: 8px; padding: 20px; background-color: #f9f9f9; text-align: center; font-family: sans-serif; overflow: hidden;">
<h3 style="margin-top: 0;">단순 조화 진동자 (Simple Harmonic Oscillator)</h3>
<div style="margin-bottom: 20px;">
<label>용수철의 고집, k: <span id="k-val">2.5</span></label><br>
<input type="range" id="k-slider" min="0.5" max="5.0" step="0.1" value="2.5" style="width: 200px;">
</div>
<div style="margin-bottom: 20px;">
<label>물체의 게으름, m: <span id="m-val">2.5</span></label><br>
<input type="range" id="m-slider" min="0.5" max="5.0" step="0.1" value="2.5" style="width: 200px;">
</div>
<div style="font-size: 1.2em; font-weight: bold; color: #333; margin-bottom: 20px;">
진동 속도 (ω) = √(k / m) = <span id="w-val">1.00</span> rad/s
</div>
<canvas id="oscillatorCanvas" width="400" height="300" style="background-color: white; border: 1px solid #ccc; border-radius: 4px; max-width: 100%;"></canvas>
</div>

<script>
const canvas = document.getElementById('oscillatorCanvas');
const ctx = canvas.getContext('2d');
const kSlider = document.getElementById('k-slider');
const mSlider = document.getElementById('m-slider');
const kVal = document.getElementById('k-val');
const mVal = document.getElementById('m-val');
const wVal = document.getElementById('w-val');
let time = 0;
let historyArr = [];

function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    
    /* 현재 k, m 값 가져오기 */
    const k = parseFloat(kSlider.value);
    const m = parseFloat(mSlider.value);
    const w = Math.sqrt(k / m);
    
    kVal.innerText = k.toFixed(1);
    mVal.innerText = m.toFixed(1);
    wVal.innerText = w.toFixed(2);
    
    /* 시간 증가 */
    time += 0.05;
    
    /* 변위 y 계산 */
    const A = 60;
    const y = A * Math.cos(w * time);
    
    /* 그래프를 위해 변위 기록 */
    historyArr.unshift(y);
    if (historyArr.length > canvas.width / 2) historyArr.pop();
    
    /* 용수철 그리기 */
    ctx.beginPath();
    ctx.moveTo(100, 0);
    ctx.lineTo(100, 100 + y);
    ctx.lineWidth = k * 1.5;
    ctx.strokeStyle = '#888';
    ctx.stroke();
    
    /* 물체 그리기 */
    const boxSize = 30 + (m * 5);
    ctx.fillStyle = '#4CAF50';
    ctx.fillRect(100 - boxSize/2, 100 + y, boxSize, boxSize);
    
    /* 파동 그래프 그리기 */
    ctx.beginPath();
    for (let i = 0; i < historyArr.length; i++) {
        const graphX = 150 + i * 2;
        const graphY = 100 + boxSize/2 + historyArr[i];
        if (i === 0) ctx.moveTo(graphX, graphY);
        else ctx.lineTo(graphX, graphY);
    }
    ctx.lineWidth = 2;
    ctx.strokeStyle = '#2196F3';
    ctx.stroke();
    
    /* 실시간 점선 연결 */
    ctx.beginPath();
    ctx.setLineDash([5, 5]);
    ctx.moveTo(100 + boxSize/2, 100 + boxSize/2 + y);
    ctx.lineTo(150, 100 + boxSize/2 + y);
    ctx.strokeStyle = '#aaa';
    ctx.stroke();
    ctx.setLineDash([]);
    
    requestAnimationFrame(draw);
}
draw();
</script>
---

## 2. Wave Equation & Standing Waves

### 2.1 Amplitude and Standing Waves
A standing wave is formed by the superposition of an incident wave propagating in the +x direction and a reflected wave propagating in the -x direction:

y(x,t) = B sin(2πx/λ) cos(ωt)

This expression combines the spatial amplitude [B sin(2πx/λ)] and the temporal amplitude [cos(ωt)], representing the interference between the right-traveling and left-traveling waves.

> **[Graph] Amplitude of a Standing Wave**
> ![정상파 그래프]({{ site.baseurl }}/assets/images/waveoptics/standingwavegraph.png)

* **Propagation Constant (Wavenumber)** k: Specifies the number of spatial periods within 2π.
  k = 2π/λ,  ω = 2π/T,  v = ω/k

### 2.2 One-Dimensional Wave Equation
For a string under tension, applying dimensional analysis to the tension T and the linear mass density ρ (mass per unit length) yields the one-dimensional wave equation:

∂²y/∂x² - (ρ/T)(∂²y/∂t²) = 0   =>   ∂²y/∂x² - (1/v²)(∂²y/∂t²) = 0

where the phase velocity is v = √(T/ρ).

> **[Graph] String Under Tension**
> ![스트링 텐션 그래프]({{ site.baseurl }}/assets/images/waveoptics/tensiongraph.png)

---

## 3. Electromagnetic Waves & Helmholtz Equation

### 3.1 Three-Dimensional Wave Equation
The one-dimensional model generalizes to a three-dimensional wave equation for a scalar field u(x,y,z,t):

∂²u/∂x² + ∂²u/∂y² + ∂²u/∂z² - (1/v²)(∂²u/∂t²) = 0   or   (∇² - (1/v²)(∂²/∂t²))u = 0

### 3.2 Electromagnetic Waves and Complex Notation
The harmonic temporal dependence of electromagnetic waves is often expressed in complex notation using the Euler formula:

U(x,y,z,t) ≡ E(x,y,z)e^(-iωt)

> **[Graph] Rotation in the Complex Plane**
> ![오일러 로테이션 그래프]({{ site.baseurl }}/assets/images/waveoptics/eulerrotationgraph.png)

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
