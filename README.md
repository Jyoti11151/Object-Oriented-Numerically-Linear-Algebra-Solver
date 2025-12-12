# Object-Oriented-Numerical-Linear-Algebra-Solver

This project implements a comprehensive object-oriented linear algebra solver using Python, integrating principles of numerical computation with modular software design. Nine core algorithms — including matrix norms, decompositions (LU, QR, SVD), least- squares systems, and iterative solvers (Jacobi, Gauss-Seidel, Conjugate Gradient) — are structured into independent classes following the SOLID principles. The objective is to demonstrate that numerical linear algebra code can be written in a reusable, extensible, and maintainable form while ensuring correctness and numerical stability. This solver can serve as a foundation for larger computational science projects.
The main goals were:
• To design an extensible and modular framework for linear algebra computation.
• To use classes and abstraction to separate algorithmic logic from user interaction.
• To implement robust matrix routines validated against analytical or NumPy results.
• To ensure maintainability and scalability for future algorithms.
The architecture is centered on a choice-based driver that dispatches execution to the correct class:
if choice == 1: MatrixNorms().run()
elif choice == 2: LDUDecomposition().run()
...
elif choice == 9: ConjugateGradient().run()
Each solver class implements three key methods: 1. get input from user() — handles input and validation.
2. solve() — performs core computation.
3. display results() — prints or verifies the result.
	The solver implements nine independent modules: 
	MatrixNorms: Computes 1, 2, ∞, and Frobenius norms. Verifies consistency between manual and NumPy calculations. 
	LDUDecomposition: Factors a square matrix into A = LDU, explicitly separat- ing scaling via D to improve numerical conditioning. 
	GramSchmidt: Implements classical Gram-Schmidt orthonormalization. Verifies orthonormality by testing QQT = I within 10−6 tolerance. 
	QRDecomposition: Uses orthogonal projection and normalization to factor A = QR. Allows numerical verification through reconstruction of A. 
	SVD: Performs Singular Value Decomposition by computing eigenvalues of AT A and AAT. Verifies that A = UΣVT. 
	LSS (Least Squares Solver): Solves overdetermined systems minx ∥Ax − b∥2 using normal equations AT Ax = AT b. Includes error norm calculation. 
	GaussJacobi: Iterative method for Ax = b using old values each iteration until convergence or tolerance threshold. 
	GaussSeidel: Successive iteration updating vector components immediately for faster convergence. 
	9. ConjugateGradient: Efficient solver for symmetric positive-definite systems min- imizing quadratic form f (x) = 12 xT Ax − bT x. Implements convergence check ∥rk∥ < ε∥r0∥.
