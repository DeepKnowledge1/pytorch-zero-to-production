
```
docs/installation.md
```

---

# ⚙️ **Environment Setup — Poetry + UV (The Right Way)**

Setting up a reliable deep learning environment can be difficult — conflicting dependencies, CUDA mismatches, messy virtual environments, and the classic *“it works on my machine”* problem.

This guide gives you a **bulletproof, modern, and reproducible PyTorch environment** using:

* **UV** → ultra-fast Python package manager & environment tool
* **Poetry** → clean dependency management & project packaging
* **PyTorch** → CPU & CUDA builds

This setup works on **Windows, macOS, and Linux**.

---

# 🚀 1. Install UV

UV is a fast, reliable package manager designed to simplify Python environments and eliminate dependency issues.

### **Windows (PowerShell)**

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### **macOS & Linux**

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

After installation, verify:

```bash
uv --version
```

---

# 🧩 2. Install Poetry

Poetry manages Python dependencies and environments in a clean, reproducible way.

### **Windows**

```powershell
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
```

### **macOS & Linux**

```bash
curl -sSL https://install.python-poetry.org | python3 -
```

Verify installation:

```bash
poetry --version
```

---

# 📦 3. Create a New Project

You can initialize a PyTorch project using **either Poetry or UV**.
Choose your preferred workflow below.

---

## 🔹 Option A — Create Project Using Poetry

```bash
poetry new my-pytorch-project
cd my-pytorch-project
poetry shell
```

Install PyTorch (CPU version):

```bash
poetry add torch torchvision
```

---

## 🔹 Option B — Create Project Using UV

```bash
uv init my-pytorch-project
cd my-pytorch-project
uv venv
```

Install PyTorch (CPU version):

```bash
uv add torch torchvision
```

---

# ⚡ 4. Install PyTorch with CUDA Support

PyTorch requires a specific index URL for GPU-enabled installations.

### **Poetry (CUDA Build)**

```bash
poetry add torch torchvision --index-url https://download.pytorch.org/whl/cu118
```

### **UV (CUDA Build)**

```bash
uv add torch torchvision --index-url https://download.pytorch.org/whl/cu118
```

> 💡 Replace **cu118** with your CUDA version if needed (e.g., cu121).

---

# 🔍 5. Verify the Installation

Run:

```bash
python -c "import torch; print(f'PyTorch version: {torch.__version__}'); print(f'CUDA available: {torch.cuda.is_available()}')"
```

Expected output:

```
PyTorch version: X.X.X
CUDA available: True/False
```

If CUDA is `True`, your GPU is correctly configured.

---

# 🛠 6. Recommended Add-Ons

Install useful development tools:

```bash
uv add numpy matplotlib jupyter
# or
poetry add numpy matplotlib jupyter
```

Start Jupyter:

```bash
jupyter notebook
```

---

# 🎉 Your Environment is Ready!

You now have a clean, modern, production-grade deep learning environment with:

* Zero dependency conflict
* Fast reproducibility
* GPU-ready PyTorch
* Professional Python workflow
* Poetry + UV synergy

This environment is the foundation for everything you’ll build in the **PyTorch Mastery Course**.
