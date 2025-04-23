---
tags:
  - UNI
  - SEM1
  - HA
date: 2025-02-17
modified: 15:52
---
## 1. Introduction
1. Time complexity
	1. matrix vector: Ax
		1. if a is sparse : O(n)
		2. if A is dense : o(mn) or O(n^2)
	2. matrix - matrix addition : A+B O(nm)
	3. Matrix - matrix multiplication : O(n^3)
2. Associativity:
	1. A.(b.c) , (a.b).c![[Pasted image 20250217160106.png]]![[Pasted image 20250217160118.png]] well it depends go which way is more efficient.
	2. matrix inversion  : o(n^3)
	3. LU (lower triangular and upper triangular matrix) : O(n^3).
	4. Cholesky Decomp : A = LL' : O(n^3).
3. the decomposition of a matrix into (rectangular) blocks and the approximation of (almost) every non-diagonal block as a rank-k matrix so that the storage requirement of the total matrix is O(nlog n) ![[Pasted image 20250217160632.png]]
4. Definition 1.5 (Rank-k matrix). A matrix A∈Rn×m with rank(A) ≤k is called rank-k matrix. If it is given in a factorization of the type A= B·CT with B ∈Rn×k, C ∈Rm×k , then we write A∈R(k) or A∈R(k,n,m).
## 2. Rank - K matrices
### Pre-req
>[!imp] imp stuff
range(M) := {Mx∈Rn |x∈Rm},
rank(M) := dim(range(M)),
0 ≤rank(M) ≤min{n,m},
rank(AB) ≤min{rank(A),rank(B)},
rank(A+ B) ≤rank(A) + rank(B),
null(M) = {x∈Rm |Mx= 0},
rank(M) + dim(null(M)) = m
### Getting the bigger picture
1. Decomposing the bigger nxm matrix to smaller nxk mxk form such that M = AB' storage is just like k(n+m)![[Pasted image 20250217185850.png]]
2. ![[Pasted image 20250217190432.png]]![[Pasted image 20250217190451.png]]![[Pasted image 20250217190704.png]]![[Pasted image 20250217190710.png]]![[Pasted image 20250217191606.png]]
### Exact operation
1. Matrix vector Multiplication M = AB' , M.x![[Pasted image 20250217192546.png]]
2. Matrix - matrix addition ![[Pasted image 20250217192759.png]]its does not increase the cost but increased the bound for the rank.
3. matrix matrix multiplication ![[Pasted image 20250217222329.png]]
### Best Approximation by rank-k Matrices
![[Pasted image 20250217234239.png]]![[Pasted image 20250217234248.png]]
error are :
- ![[Pasted image 20250217235007.png]]
Difference between Full and reduced SVD. ==21n^3==
![[Pasted image 20250217234320.png]]

### Best approximatin of Rank l by rank K matrices.
1. QR decomposition : ==4nm^2== ![[Pasted image 20250218001045.png]]
2. Truncation from rank L to rank K![[Pasted image 20250218001835.png]]proof of that![[Pasted image 20250218001913.png]]computation cost ![[Pasted image 20250218015108.png]]![[Pasted image 20250218015122.png]]computation cost : l-> k is 22ℓ^3+4ℓ^2(n+m)+2kℓ(n+m) 
3. Rank K matrix addition with trucation
	1. ![[Pasted image 20250218015547.png]]
4. Agglomeratoin of Rank K matrices.
	1. hows its done?![[Pasted image 20250218020014.png]]
	2. Cost comparison wrt to truncation:
		1. Truncation ![[Pasted image 20250218021013.png]]![[Pasted image 20250218021023.png]]
		2. Agglomeration ![[Pasted image 20250218021041.png]]
	3. 
	
## Special H-Matrix structure.
![[Pasted image 20250218142942.png]]
- storage cost of Hp matrices![[Pasted image 20250218143221.png]]
- Matrix vector multiplication ![[Pasted image 20250218143958.png]]
- matrix matrix addition ![[Pasted image 20250218144611.png]]![[Pasted image 20250218144639.png]]
- matrix matrix multiplication. ![[Pasted image 20250218144808.png]]![[Pasted image 20250218144813.png]]
- matrix inversion ![[Pasted image 20250218145043.png]]![[Pasted image 20250218145055.png]]
- LU decomposition ![[Pasted image 20250218145124.png]]
- One dimensional Integral equation model problem.![[Pasted image 20250218173353.png]]



