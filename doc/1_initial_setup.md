# Initial Project Setup Documentation

Movie Correlation Analysis (Python)

This document records every step taken to set up the development
environment and notebook for this project. It is intended to show clear,
reproducible setup steps and good engineering practice.

------------------------------------------------------------------------

## 1. Project Folder Structure

The project was structured in a simple, beginner-friendly way:

``` text
python-movie-correlation-project/
├─ data/
│  └─ movies.csv
├─ doc/
│  └─ initial_setup.md
├─ notebook/
│  └─ movie_correlation.ipynb
├─ images/
└─ README.md
```

This structure keeps raw data, documentation, notebooks, and outputs clearly separated.

------------------------------------------------------------------------

## 2. Python Version Verification

The Python version was checked to ensure compatibility with data
analysis libraries.

``` bash
python3 --version
```

Output confirmed Python 3.12.3 was installed.

------------------------------------------------------------------------

## 3. Handling macOS Package Management (PEP 668)

When attempting to install or upgrade packages globally, macOS returned
an\
`externally-managed-environment` error. This is expected behaviour on
modern macOS systems using Homebrew.

To avoid breaking the system Python installation, a **virtual
environment** was created for the project.

------------------------------------------------------------------------

## 4. Creating a Virtual Environment

A project-specific virtual environment was created in the project root:

``` bash
python3 -m venv .venv
```

This created a `.venv/` folder containing an isolated Python
environment.

------------------------------------------------------------------------

## 5. Activating the Virtual Environment

The virtual environment was activated before installing any packages:

``` bash
source .venv/bin/activate
```

Once activated, the terminal prompt showed `(.venv)` to confirm the
environment was active.

------------------------------------------------------------------------

## 6. Installing Required Libraries

All required libraries were installed **inside the virtual
environment**:

``` bash
pip install pandas numpy matplotlib seaborn jupyter
```

This ensured the project dependencies were isolated and reproducible.

------------------------------------------------------------------------

## 7. Verifying Installed Packages

Installed packages were verified using:

``` bash
pip list | grep -E "pandas|numpy|matplotlib|seaborn|jupyter"
```

Confirmed installations included: - pandas - numpy - matplotlib -
seaborn - jupyter / jupyterlab

------------------------------------------------------------------------

## 8. Selecting the Correct Python Interpreter in VS Code

To ensure Jupyter used the project virtual environment:

1.  Opened `movie_correlation.ipynb`

2.  Clicked **Select Kernel** (top right of the notebook)

3.  Chose:

        Python 3.12.3 (.venv)

4.  Confirmed the kernel indicator showed `.venv`

This step is critical so the notebook uses the correct installed
libraries.

------------------------------------------------------------------------

## 10. Initial Notebook Setup and Verification

The first code cell in the notebook was used to confirm the environment
worked correctly:

``` python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

print("Notebook setup OK")
```

Successful execution confirmed: - Kernel selection was correct -
Libraries were available - Notebook was ready for analysis

------------------------------------------------------------------------

## 11. Loading the Dataset

The dataset was loaded from the `data/` folder and previewed:

``` python
df = pd.read_csv("../data/movies.csv")
df.head()
```

This confirmed: - File paths were correct - The dataset loaded
successfully - Columns such as `budget`, `gross`, `votes`, `company`,
and `released` were present

------------------------------------------------------------------------

## Status

At this point, the project setup is complete.\
The notebook is fully operational and ready for data analysis.
