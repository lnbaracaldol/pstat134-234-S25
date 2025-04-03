# Environment Setup and RStudio Configuration Manual

Welcome! This manual will help you set up your Python and R environment for running Quarto projects that integrate both languages.

------------------------------------------------------------------------

## 1. Creating and Activating a Conda Environment (via Terminal)

To create a new conda environment named `ds-env` with Python:

``` bash
conda create -n ds-env python=3.12
```

To activate the environment:

``` bash
conda activate ds-env
```

To deactivate the environment:

``` bash
conda deactivate
```

------------------------------------------------------------------------

### Conda Commands Cheat Sheet

| **Command**                                 | **Description**                                         |
|----------------------------|--------------------------------------------|
| `conda --version`                           | Check installed Conda version                           |
| `conda info`                                | Show information about current Conda setup              |
| `conda list`                                | List packages in the current environment                |
| `conda create -n env_name`                  | Create a new environment                                |
| `conda create -n env_name python=3.10`      | Create env with specific Python version                 |
| `conda activate env_name`                   | Activate an environment                                 |
| `conda deactivate`                          | Deactivate current environment                          |
| `conda env list`                            | List all environments                                   |
| `conda install package_name`                | Install a package into the active environment           |
| `conda install -c conda-forge package_name` | Install from a specific channel (e.g., conda-forge)     |
| `conda remove package_name`                 | Remove a package from the active environment            |
| `conda update package_name`                 | Update a package                                        |
| `conda env remove -n env_name`              | Delete an environment                                   |
| `conda list -e > requirements.txt`          | Export environment to a requirements file               |
| `conda env export > env.yaml`               | Export full environment (including versions & channels) |
| `conda env create -f env.yaml`              | Create env from exported YAML file                      |

------------------------------------------------------------------------

------------------------------------------------------------------------

## 2. Installing Required Packages (via Terminal)

After activating your environment, you can install packages using `conda` or `pip`:

``` bash
conda install numpy pandas matplotlib
# or
pip install numpy pandas matplotlib
```

You can specify versions if needed:

``` bash
pip install torch==1.13.1
```

If you encounter errors due to version conflicts, try: - Googling the error messages - Downgrading or upgrading specific packages - Using `conda-forge` for compatibility

------------------------------------------------------------------------

## 3. RStudio Settings for Python Integration

1.  Open **RStudio**
2.  Go to **Tools** → **Global Options**
3.  On the left, click **Python**
4.  Browse and choose your conda environment (`ds-env`) or Python interpreter path (e.g., `/home/user/miniconda3/envs/ds-env/bin/python`)
5.  Click **Apply**

------------------------------------------------------------------------

## 4. Using Python in RStudio with Quarto

Install the `reticulate` package in R:

``` r
install.packages("reticulate")
```

Load it whenever needed, and you can link yout Python environment:

``` r
library(reticulate)
use_condaenv("ds-env")
```

### Writing Python in `.qmd` (Quarto) Files

To run Python code inside Quarto:

```` markdown
```{python}
# Your Python code here
import numpy as np
np.mean([1, 2, 3])
```
````

You can also install Python packages from within the terminal of RStudio using `pip`:

```` markdown
```{bash}
pip install seaborn
```
````

Or you can install Python packages from within R:

```` markdown
```{r}
reticulate::py_require("xgboost")
```
````

------------------------------------------------------------------------

Happy coding!





