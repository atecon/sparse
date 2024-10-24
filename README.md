This package contains a few elementary functions that could be useful
# Sparse Matrices

When you have "sparse" matrices, that is, matrices which mostly contain zeros, such matrices are turned into special-purpose bundles, whose elements are:

- **r**: rows (scalar)
- **c**: columns (scalar)
- **nz**: number of non-zero entries (scalar)
- **v**: vector containing non-zero entries (matrix)
- **pos**: 2-column matrix with the positions of non-zero entries (matrix)

You turn a matrix into a sparse matrix bundle via the function `m2sp()`. The inverse function is called `sp2m()`. Alternatively, you can create an empty (zero) matrix via the `spinit(r, c)` function and then populate it via the `spelemset()` function. The function `spprint` prints it out, with an optional extra boolean argument to print it like a regular matrix. For example:

```hansl
A = zeros(4,3)
A[2,3] = 1
A[1,3] = 6
Y = m2sp(A)

X = spinit(6,2)
spelemset(&X, 3, 1, 11)
spelemset(&X, 6, 2, -4)

spprint(Y)
spprint(X, 1)
```

Produces:

```
Y is (4 x 3)

         1         3         6
         2         3         1

X (as matrix)

         0         0
         0         0
        11         0
         0         0
         0         0
         0        -4
```

Other functions contained in the package are:

- `spelemget(bundle X, scalar r, scalar c)`: returns the scalar `X[r,c]`
- `sprowget(bundle X, scalar r)`: returns the r-th row of `X`
- `spcolget(bundle X, scalar c)`: returns the c-th column of `X`
- `sptran(bundle X)`: returns the transpose of `X` as a sparse matrix bundle
- `spscalmult(bundle X, scalar a)`: returns `(X * a)` as a sparse matrix bundle
- `sphcat(bundle A, bundle B)`: returns `(A ~ B)` as a sparse matrix bundle
- `spvcat(bundle A, bundle B)`: returns `(A | B)` as a sparse matrix bundle
- `spadd(bundle A, bundle B)`: returns `(A + B)` as a sparse matrix bundle
- `spmult(bundle A, bundle B)`: returns `(A * B)` as a sparse matrix bundle

## Changelog

- **1.0 -> 1.01**: Fix Boolean "="
