---
title: "Assignment1"
date: 2025-03-25
---

# Matrix Multiplication Project Report

**Student Name**: [liziao]  
**Student ID**: [ZY2457B15]  
**Submission Date**: [2025/3/25]


## System Configuration
List your system configuration as **table of content here** here, including CPU model, memory size, operating system version, compiler version, python version.

For Linux, check

-  **CPU Model**: Intel(R) Xeon(R) Platinum 8352V CPU @ 2.10GHz
-  **Memory Size**: 503 GiB
-  **Operating System Version**: Ubuntu 5.15.0-94-generic (x86_64)
-  **Compiler Version**: GCC 9.4.0
-  **Python Version**: Python 3.8.10

## Implementation Details

### C Language Implementation
-  **Source Code**: 
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>  
// Function: Perform matrix multiplication C = A * B
// A: m x n, B: n x p, C: m x p
void matrix_multiply(double** A, double** B, double** C, int m, int n, int p) {
    int i, j, k;
    // Triple nested loops for matrix multiplication
    for (i = 0; i < m; i++) {
        for (j = 0; j < p; j++) {
            C[i][j] = 0.0;  // Initialize
            for (k = 0; k < n; k++) {
                C[i][j] += A[i][k] * B[k][j];
            }
        }
    }
}

int main() {
    // Example: A is 2x3, B is 3x2
    int m = 2, n = 3, p = 2;
    int i, j;

    // Dynamically allocate matrices A, B, C
    double** A = (double**)malloc(m * sizeof(double*));
    double** B = (double**)malloc(n * sizeof(double*));
    double** C = (double**)malloc(m * sizeof(double*));

    for (i = 0; i < m; i++) {
        A[i] = (double*)malloc(n * sizeof(double));
    }
    for (i = 0; i < n; i++) {
        B[i] = (double*)malloc(p * sizeof(double));
    }
    for (i = 0; i < m; i++) {
        C[i] = (double*)malloc(p * sizeof(double));
    }

    // Initialize matrix A (2x3)
    double tempA[2][3] = {
        {1.0, 2.0, 3.0},
        {4.0, 5.0, 6.0}
    };
    for (i = 0; i < m; i++) {
        for (j = 0; j < n; j++) {
            A[i][j] = tempA[i][j];
        }
    }

    // Initialize matrix B (3x2)
    double tempB[3][2] = {
        {7.0,  8.0},
        {9.0,  10.0},
        {11.0, 12.0}
    };
    for (i = 0; i < n; i++) {
        for (j = 0; j < p; j++) {
            B[i][j] = tempB[i][j];
        }
    }

    // Start timing (using clock())
    clock_t start_time = clock();

    // Compute matrix multiplication C = A * B
    matrix_multiply(A, B, C, m, n, p);

    // End timing
    clock_t end_time = clock();
    double elapsed_time = (double)(end_time - start_time) / CLOCKS_PER_SEC;

    // Print the resulting matrix C
    printf("The resulting matrix A x B (2x2):\n");
    for (i = 0; i < m; i++) {
        for (j = 0; j < p; j++) {
            printf("%.2f ", C[i][j]);
        }
        printf("\n");
    }

    // Print the time taken
    printf("Time taken for C matrix multiplication: %.6f seconds\n", elapsed_time);

    // Free allocated memory
    for (i = 0; i < m; i++) {
        free(A[i]);
    }
    free(A);

    for (i = 0; i < n; i++) {
        free(B[i]);
    }
    free(B);

    for (i = 0; i < m; i++) {
        free(C[i]);
    }
    free(C);

    return 0;
}

```
-  **Compilation Command**:
```gcc matrix_mul.c -o matrix_mul```

-  **Execution Command**: 
```./matrix_mul```

### Python Language Implementation
-  **Source Code**:
```
import time
def matrix_multiply(A, B):
    """
    Calculate the product of matrix A and matrix B, and return the resulting matrix.
    Assumptions:
        - A is an m × n matrix
        - B is an n × p matrix
    Hence, the resulting matrix C is an m × p matrix.
    """
    m = len(A)
    n = len(A[0])
    p = len(B[0])

    # Initialize the result matrix C (size: m × p) with zeros
    C = [[0 for _ in range(p)] for _ in range(m)]

    # Triple nested loops for matrix multiplication
    for i in range(m):
        for j in range(p):
            for k in range(n):
                C[i][j] += A[i][k] * B[k][j]

    return C

if __name__ == "__main__":
    A = [
        [1, 2, 3],
        [4, 5, 6]
    ]  # 2 x 3

    B = [
        [7,  8],
        [9,  10],
        [11, 12]
    ]  # 3 x 2

    # Start timing
    start_time = time.time()

    # Perform matrix multiplication
    C = matrix_multiply(A, B)

    # End timing
    end_time = time.time()
    elapsed_time = end_time - start_time

    # Print the result
    print("Matrix A × B:")
    for row in C:
        print(row)

    # Print the elapsed time
    print(f"Time taken for Python matrix multiplication: {elapsed_time:.6f} seconds")

```
-  **Execution Command**: 
```
python matrix_mul.py
```

## Algorithm Verification
-  **Correctness**: 
test matrix A:
```
[7, 8],
[9, 10],
[11,12]
```
test matrix B:
```
[1, 2, 3],
[4, 5, 6]
```
result for c:
```
The resulting matrix A x B (2x2):
58.00 64.00 
139.00 154.00 
```
result for python:
```
The result of matrix A × matrix B is:
[58, 64]
[139, 154]
```

## Performance Analysis【bonus】
-  **Execution Times**: 
Time taken for C matrix multiplication: 0.000003 seconds
Time taken for Python matrix multiplication: 0.000016 seconds

-  **Analysis**: 
Python is an interpreted language, which comes with the overhead of the interpreter itself as well as its runtime scheduling. Invoking functions, creating lists, and other operations all involve additional overhead at the Python layer.
C is a compiled language that generates machine code directly, allowing it to execute more efficiently at runtime and operate closer to the hardware.

## Conclusion
Through this project, I learned how to compile and run different types of programming languages in a Linux environment, and I also learned how to use Markdown for documentation.

## References

## Appendix
