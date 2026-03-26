# Vector Calculus: Velocity and Acceleration

This document provides the step-by-step solution for finding the velocity and acceleration vectors from a given position function.

## Problem Statement
The position of an object is given by:
$$\vec{r}(t) = (3t^2)\hat{i} + (5t - 8t^2)\hat{j}$$

Find the object's **velocity** and **acceleration** vectors as a function of time.

---

## 1. Velocity Vector $\vec{v}(t)$
Velocity is defined as the first derivative of the position vector with respect to time:
$$\vec{v}(t) = \frac{d\vec{r}}{dt}$$

To find it, we differentiate each component separately:
*   **x-component:** $\frac{d}{dt}(3t^2) = 6t$
*   **y-component:** $\frac{d}{dt}(5t - 8t^2) = 5 - 16t$

**Result:**
$$\vec{v}(t) = (6t)\hat{i} + (5 - 16t)\hat{j}$$

---

## 2. Acceleration Vector $\vec{a}(t)$
Acceleration is the derivative of the velocity vector (the second derivative of position):
$$\vec{a}(t) = \frac{d\vec{v}}{dt}$$

We differentiate the velocity components found above:
*   **x-component:** $\frac{d}{dt}(6t) = 6$
*   **y-component:** $\frac{d}{dt}(5 - 16t) = -16$

**Result:**
$$\vec{a}(t) = 6\hat{i} - 16\hat{j}$$

---

## Summary of Results

| Vector | Formula |
| :--- | :--- |
| **Position** | $\vec{r}(t) = (3t^2)\hat{i} + (5t - 8t^2)\hat{j}$ |
| **Velocity** | $\vec{v}(t) = (6t)\hat{i} + (5 - 16t)\hat{j}$ |
| **Acceleration** | $\vec{a}(t) = 6\hat{i} - 16\hat{j}$ |

> **Note:** Since the acceleration vector does not contain the variable $t$, the object is moving with **constant acceleration**.
