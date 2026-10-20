------------------------------------------------------------------------

# Introduction to Machine Learning course 2026-2027

## Applied Bioinformatics Division, DKFZ.

Welcome to the course exercises. Here you will find relevant information as of how to set-up the python libraries needed for the exercises, as well as an introductory script to familiarize yourself with some basic python code we will use throughout the course.

## Getting started

Requirements

- Python 3.10 or newer (tested with Python 3.13)
- 8 GB of RAM (recommended)

Check your Python version:

``` bash
python3 --version   # macOS / Linux
python --version    # Windows
```

## IDE: Visual Studio Code

We recommend [Visual Studio Code](https://code.visualstudio.com/) as the IDE for this course. After installing it, open the **Extensions** panel (`Ctrl+Shift+X` / `Cmd+Shift+X`) and install the **Python** and **Jupyter** extensions from Microsoft. With these you can open and run the `.ipynb` notebooks directly in VS Code, and use its built-in terminal (**Terminal \> New Terminal**) to run the installation commands below.

## Installation (Python virtual environment)

**1. Go to the course folder**

``` bash
cd path/to/the/course/folder
```

**2. Create the virtual environment** (a folder called `scrna_env`)

``` bash
# macOS / Linux
python3 -m venv scrna_env

# Windows
python -m venv scrna_env
```

**3. Activate it** (do this every time you open a new terminal)

``` bash
# macOS / Linux
source scrna_env/bin/activate

# Windows (Command Prompt)
scrna_env\Scripts\activate

# Windows (PowerShell)
scrna_env\Scripts\Activate.ps1
```

Your prompt should now start with `(scrna_env)`.

**4. Install all packages**

``` bash
python -m pip install --upgrade pip
pip install numpy pandas scipy matplotlib seaborn scanpy anndata h5py umap-learn pynndescent numba scikit-learn jupyterlab ipykernel
```

**5. Register the environment as a Jupyter kernel**

``` bash
python -m ipykernel install --user --name scrna_env --display-name "Python (scrna_env)"
```

**6. Check that everything works**

``` bash
python -c "import scanpy, seaborn, umap, sklearn; print('scanpy', scanpy.__version__)"
```

If it prints the scanpy version without errors, you are ready.

**7. Open the notebook**

- **In VS Code:** open the course folder (**File \> Open Folder**), open the notebook, click **Select Kernel** (top right) and choose `scrna_env` / `Python (scrna_env)`.
- **In the browser:** run `jupyter lab` and select the kernel `Python (scrna_env)` (**Kernel \> Change Kernel**).

When you are done, you can deactivate the environment with `deactivate`.

### Troubleshooting

- **`Failed to build wheels for numba / llvmlite`**: your Python version is probably too new for the available numba packages. Install pre-built packages only with `pip install --only-binary=:all: numba llvmlite`, or create the environment with an older Python (e.g. 3.12).
- **`ModuleNotFoundError: No module named 'scanpy'` in the notebook**: the notebook is not using the environment's kernel. Repeat step 5 and select `Python (scrna_env)` as the kernel.
- **The kernel crashes ("kernel died")**: close other programs to free memory and restart the kernel.

# Machine Learning course – single-cell RNA-seq exercises

Exercises based on a single-cell RNA-seq dataset of human breast tissue from the [Tabula Sapiens](https://tabula-sapiens-portal.ds.czbiohub.org/) consortium.

## Files

| File | Description |
|------------------------------------|------------------------------------|
| `01_scRNAseq_breast_exploration_QC.ipynb` | Introductory notebook: data exploration, quality control, PCA/UMAP and marker genes |
| `tabula_sapiens_breast_counts.h5ad` | Dataset (raw counts, \~15,000 cells from 2 donors) |

Keep both files in the same folder.

Start with the notebook **`01_scRNAseq_breast_exploration_QC.ipynb`**, which serves as the introduction to the course. Go through it cell by cell: it shows how single-cell data are stored, how to explore and quality-check them, and how to normalise and visualise them with PCA and UMAP. Read the explanations and try to run each cell. The processed dataset that the script saves at the end (`tabula_sapiens_breast_processed.h5ad`) will be used in the following exercises.
