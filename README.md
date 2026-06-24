# MATLAB Numerical Methods Programs

A collection of MATLAB programs for solving numerical and algebraic problems using various numerical methods.

---

## 1. Bisection Method

### Problem Statement
Find the root of:

\[
x^2 - 2 = 0
\]

### MATLAB Code

```matlab
% BISECTION METHOD

clc;
clear all;

f = @(x) (x^2 - 2);

a = 1;
b = 2;
tol = 1e-2;

if f(a)*f(b) < 0
    fprintf('we can proceed\n');
else
    fprintf('we cannot proceed');
end

i = 0;

while abs(a-b) > tol
    c = (a+b)/2;
    i = i+1;

    if f(c)*f(a) < 0
        b = c;
    else
        a = c;
    end
end

c
i
```

---

## 2. Fixed Point Iteration Method

### Problem Statement
Solve:

\[
x^2 - x - 2 = 0
\]

using

\[
x = \sqrt{x+2}
\]

### MATLAB Code

```matlab
% FIXED POINT METHOD

clc;
clear all;

g = @(x) (sqrt(x+2));

x0 = 1;
tol = 1e-2;
N = 1000;

i = 1;

while i < N

    x1 = g(x0);

    if abs(x1-x0) < tol
        break;
    else
        x0 = x1;
    end

    i = i+1;

end

x1
i
```

---

## 3. Newton-Raphson Method

### Problem Statement

Find the root of:

\[
x^2 - 2 = 0
\]

### MATLAB Code

```matlab
% NEWTON RAPHSON METHOD

clc;
clear all;

f = @(x) x^2 - 2;

g = @(x) 2*x;

x0 = 1.5;

N = 1000;
tol = 10^-2;

i = 1;

while i < N

    x1 = x0 - f(x0)/g(x0);

    if abs(x0-x1) < tol
        break;
    else
        x0 = x1;
    end

    i = i+1;

end

x1
i
```

---

## 4. Gaussian Elimination Method

### Problem Statement

Solve the system:

\[
x_1+x_2+x_3=6
\]

\[
2x_1+x_2+x_3=14
\]

\[
x_1+2x_2+3x_3=14
\]

### MATLAB Code

```matlab
% GAUSSIAN ELIMINATION METHOD

clc;
clear all;

A = [1 1 1 6;
     2 1 1 14;
     1 2 3 14];

n = 3;

for i = 1:n-1
    for j = i+1:n

        k = A(j,i)/A(i,i);
        A(j,:) = A(j,:) - k*A(i,:);

    end
end

x = zeros(n,1);

x(n) = A(n,n+1)/A(n,n);

for i = n-1:-1:1

    sum = 0;

    for j = i+1:n
        sum = sum + A(i,j)*x(j);
    end

    x(i) = (A(i,n+1)-sum)/A(i,i);

end

x
```

---

## 5. Gauss-Seidel Method

### Problem Statement

Solve the system:

\[
4x_1+2x_2+x_3=14
\]

\[
x_1+5x_2+x_3=10
\]

\[
x_1+x_2+8x_3=20
\]

### MATLAB Code

```matlab
% GAUSS SEIDEL METHOD

n = 3;

A = [4 2 1;
     1 5 1;
     1 1 8];

b = [14;10;20];

x0 = [1,1,1];
x1 = zeros(n,1);

k = 0;
N = 1000;
tol = 10^-4;

while k < N

    for i = 1:n

        sum = 0;

        for j = 1:i-1
            sum = sum + A(i,j)*x1(j);
        end

        for j = i+1:n
            sum = sum + A(i,j)*x0(j);
        end

        x1(i) = (b(i)-sum)/A(i,i);

    end

    if norm(x0-x1,inf) < tol
        break
    else
        x0 = x1;
        k = k + 1;
    end

end

x1
k
```

---

## 6. Newton-Raphson Method for System of Nonlinear Equations

### Problem Statement

Solve:

\[
x_1^2+x_2^2-4=0
\]

\[
x_1^2-x_2^2-1=0
\]

### MATLAB Code

```matlab
% NEWTON RAPHSON METHOD FOR SYSTEM OF EQUATIONS

clc;
clear all;

f = @(x)[x(1)^2+x(2)^2-4;
         x(1)^2-x(2)^2-1];

J = @(x)[2*x(1)  2*x(2);
         2*x(1) -2*x(2)];

tol = 10^-2;

x0 = [1;1];

k = 1;
N = 1000;

while k < N

    y = inv(J(x0))*f(x0);

    x1 = x0-y;

    if norm(y) < tol
        break
    else
        x0 = x1;
    end

    k = k + 1;

end

x1
```

---

## Methods Included

- Bisection Method
- Fixed Point Iteration Method
- Newton-Raphson Method
- Gaussian Elimination Method
- Gauss-Seidel Method
- Newton-Raphson Method for Systems of Nonlinear Equations

## Software Used

- MATLAB R2016a or later
