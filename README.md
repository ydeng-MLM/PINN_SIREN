# 2D Helmholtz PINN with SIREN

This repository contains a Physics-Informed Neural Network (PINN) implementation to solve the 2D Helmholtz equation using a sinusoidal representation network (SIREN). The model is built and trained in **PyTorch**, and the notebook is designed to run in **Google Colab**.

## 📘 Problem Overview

We solve the following PDE:
\[
-\nabla^2 u(x, y) - k_0^2 u(x, y) = f(x, y)
\]
- Complex-valued solution: \( u(x, y) = \text{Re}(u) + i \, \text{Im}(u) \)
- Point source \( f(x, y) = i \omega \delta(x - x_0, y - y_0) \)
- Open boundary conditions on all edges: \(\frac{\partial u}{\partial n} + i k_0 u = 0\)

## 🔬 Features

- **SIREN (Sinusoidal Representation Network)** for high-frequency solution modeling
- Point source at arbitrary location (default: \((-L/4, L/4)\))
- Circular inclusion with higher permittivity \( \varepsilon = 2 \) at the center
- Automatically handles spatially varying \( \varepsilon(x, y) \)
- Visualizations for:
  - Real part, Imaginary part, and Amplitude of predicted field
  - Comparison with analytical solution via Hankel function (Green's function)

## 🧠 Tech Stack

- Python + PyTorch
- Google Colab-compatible
- Visualization with Matplotlib
- Analytical solution from `scipy.special.hankel1`

## 📝 Files

- `PINN_quick_test.ipynb` — Main Colab notebook
- `README.md` — You are here


## 🧪 How to Use

1. Open `PINN_quick_test.ipynb` in Google Colab.
2. Run all cells to train the PINN and visualize results.
3. Modify:
   - Point source location
   - Circle radius / permittivity
   - Network architecture

## 📌 TODO

- [ ] Export trained model
- [ ] Allow arbitrary-shaped permittivity
- [ ] Add complex-field learning

## 📖 Reference

- SIREN paper:
```
@inproceedings{sitzmann2019siren,
    author = {Sitzmann, Vi\ncent
              and Martel, Julien N.P.
              and Bergman, Alexander W.
              and Lindell, David B.
              and Wetzstein, Gordon},
    title = {Implicit Neural Representations
              with Periodic Activation Functions},
    booktitle = {arXiv},
    year={2020}
}
```
- PINNs:
```
@article{lu2021deepxde,
  author  = {Lu, Lu and Meng, Xuhui and Mao, Zhiping and Karniadakis, George Em},
  title   = {{DeepXDE}: A deep learning library for solving differential equations},
  journal = {SIAM Review},
  volume  = {63},
  number  = {1},
  pages   = {208-228},
  year    = {2021},
  doi     = {10.1137/19M1274067
}
```

---

Feel free to fork, modify, and use this for solving other wave propagation or inverse design problems using PINNs!
