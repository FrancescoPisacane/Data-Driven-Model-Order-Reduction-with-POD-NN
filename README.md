# Data-Driven-Model-Order-Reduction-with-POD-NN

## Leakage Detection in a Water Reservoir

This repository presents a data-driven approach for leakage detection in a water reservoir, utilizing advanced Model Order Reduction (MOR) techniques. The project's core is the development of a surrogate model based on **Proper Orthogonal Decomposition (POD)** and **Neural Networks (NN)** to efficiently approximate the complex pressure field governed by the underlying Partial Differential Equations (PDEs). This methodology effectively bypasses the computational cost of solving high-fidelity Finite Element Method (FEM) simulations, providing a fast and accurate solution for parameter estimation.

## Key Features and Methodologies

- **Dataset Utilization**: The project is built upon a pre-computed dataset of high-fidelity FEM simulations, which serves as the "truth data" to train and validate our reduced-order model. The dataset maps a set of parameters (leakage location and size) to the corresponding full-state pressure field.
- **Data-Driven ROM Implementation**: I implemented a **POD-NN** (Proper Orthogonal Decomposition - Neural Network) framework. This technique leverages POD to find an optimal low-dimensional basis (the POD modes) for the high-dimensional data, followed by a neural network that learns the nonlinear mapping from the model parameters to the POD coefficients.
- **ROM Training and Assessment**: The POD-NN model was trained on a subset of 150 simulations and rigorously assessed on a test set of 50 unseen simulations. I quantified the model's performance by computing the average relative error in the $L^2$ norm, achieving an accuracy well below the target threshold of 12%, demonstrating the surrogate model's predictive power.
- **Inverse Problem Solving**: The trained ROM is then used to solve a crucial inverse problem: estimating the model parameters (leakage characteristics) from sparse sensor measurements. This is formulated as a least-squares minimization problem. Leveraging the ROM, this optimization is solved orders of magnitude faster than with the full FEM model. For instance, estimating parameters for **1000 simulations** can be reduced from approximately **two hours** down to just **30 seconds**.
- **Code Structure**: The entire workflow is documented and implemented within a single, interactive Jupyter Notebook (`POD_NN.ipynb`), ensuring a clear, step-by-step execution. To foster readability and smooth online execution, the trained ROM is saved and loaded, eliminating the need for time-consuming retraining.

## Tools and Libraries

- **Python**: The project is implemented in Python, the de facto standard for machine learning and scientific computing.
- **`dlroms` Library**: I used the `dlroms` library, a dedicated tool for implementing data-driven ROMs, which streamlined the development process.
- **Jupyter Notebook**: For interactive development, code execution, and rich visualization of results.

## Who is this repository for

This repository is an excellent resource for students, researchers, and practitioners in computational science and engineering. It provides a practical, state-of-the-art example of how machine learning and MOR can be combined to solve challenging inverse problems in fields like structural health monitoring, fluid dynamics, and geophysics.
