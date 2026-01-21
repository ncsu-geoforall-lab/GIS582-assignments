# NCSU GIS582 — 2. Geospatial Data Models and Visualization

## Overview

Please visit the course website for full details:
[https://ncsu-geoforall-lab.github.io/geospatial-modeling-course/topics/data_models_visu.html](https://ncsu-geoforall-lab.github.io/geospatial-modeling-course/topics/data_models_visu.html)

## Repository structure

The easiest way to run this assignment is using Google Colab. Click the badges below to open the tutorial and assignment notebooks in Colab.

### Colab Notebooks

#### Tutorial

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ncsu-geoforall-lab/GIS582-assignments/blob/main/2AB%20-%20Geospatial%20Data/2A_Tutorial.ipynb)

#### Assignment

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ncsu-geoforall-lab/GIS582-assignments/blob/main/2AB%20-%20Geospatial%20Data/2A_Assignment.ipynb)

### Local Notebooks

If you prefer to run the notebooks locally, clone this repository and open the notebooks in JupyterLab or Jupyter Notebook.

When running locally, you can delete or skip the set up cells for Google Colab. Start with the __GRASS Setup__ section.

__*Windows Users:* You will need to make additional modifications to get this notebook to run.__

1. `%%bash` only works on unix machines (i.e. Mac and Linux). You will need to replace this with `!` in front of each terminal command. For example,:

    ```bash
    %%bash
    g.region res=100 -p
    r.resamp.stats elev_ned_30m out=elev_new100m_avg method=average
    ```

    Should be reformatted:

    ```bash
    !g.region res=100 -p
    !r.resamp.stats elev_ned_30m out=elev_new100m_avg method=average
    ```

2. On Windows machines, the GRASS executable is called `grass84` or `grass85` instead of `grass`. During GRASS Setup, replace the "Ask GRASS where its Python packages are" with:

    ```python
    # Ask GRASS GIS where its Python packages are.
    sys.path.append(
        subprocess.check_output(["grass84", "--config", "python_path"], text=True, shell=True).strip()
    )
    ```

    Note that in addition to changing the `grass` call,  `subprocess.check_output()` behaves slightly differently and needs the `shell=True` keyword argument.

3. Similarly, when downloading the sample project, change the `path` and the GRASS executable name:

    ```bash
    !grass84 --tmp-project XY --exec g.download.project url=https://grass.osgeo.org/sampledata/north_carolina/nc_spm_08_grass7.tar.gz path="C:\YOUR\PATH\HERE\"
    ```

    For the path, here is an example path `C:\Users\chaedri\Documents\GIS582\`. In this GIS882 directory, you could also have this github repository stored. In this configuration, you could launch GRASS in Assignment 2A with `gj.init("../../nc_spm_08_grass7/user1")` or with `gj.init("C:\Users\chaedri\Documents\GIS582\nc_spm_08_grass7/user1")`.

### Requirements

- [GRASS 8.4.1 or later installed with Python support](https://grass.osgeo.org/download/).
- Python >=3.8 (Tested with 3.12.12)
- [JupyterLab or Jupyter Notebook installed](https://jupyter.org/install).

## Contact

Author: Corey White or Helena Mitasova. For course questions, follow instructor guidelines.

<!-- ## Citation

If you use this material in your research, please cite:

White, C., Mitasova, H., Haedrich, C., Petrasova, A., Regmi, P., & Petras, V. (2024). GIS582-assignments: Jupyter Notebooks for Geospatial Modeling and Analysis course. GeoForAll Lab, North Carolina State University. -->
