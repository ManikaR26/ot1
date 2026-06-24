# MATLAB Optimization Programs

---

## 4. Gauss-Seidel Method

### Problem Statement

Solve the following system of linear equations using the Gauss-Seidel Iterative Method:

\[
4x_1 + 2x_2 + x_3 = 14
\]

\[
x_1 + 5x_2 + x_3 = 10
\]

\[
x_1 + x_2 + 8x_3 = 20
\]

### MATLAB Code

```matlab
n = 3; % no. of rows

A = [4 2 1;
     1 5 1;
     1 1 8];

b = [14; 10; 20];

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

        x1(i) = (b(i) - sum)/A(i,i);

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

tive technique used to solve systems of linear equations. Unlike the Jacobi Method, newly computed values are immediately used in subsequent calculations within the same iteration, resulting in faster convergence for diagonally dominant matrices.
