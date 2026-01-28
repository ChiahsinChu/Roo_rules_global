# How to contribute to conda-forge

> [Official Guideline](https://conda-forge.org/docs/maintainer/adding_pkgs/)

## Staging process (add recipe and license)

1. install `grayskull`

   ```bash
   conda install -c conda-forge grayskull
   ```

2. generate recipes from grayskull

   ```bash
   git checkout -b $PKG_NAME
   cd recipes/
   grayskull pypi $PKG_NAME --maintainers ChiahsinChu --strict-conda-forge
   ```

3. modify the recipes (`meta.yaml`) from grayskull
   - Use [SPDX](https://spdx.org/licenses/) identifier for license (e.g., LGPL-3.0-or-later).
   - Set `{% set python_min = "3.10" %}`
   - For the host section of the recipe, use the pin `python {{ python_min }}` for the python entry.
   - For the run section of the recipe, use the pin `python >={{ python_min }}` for the python entry.
   - For the test.requires section of the recipe, use the pin `python {{ python_min }}` for the python entry.
   - Set about.home:
     ```yaml
     about:
       home: https://github.com/ChiahsinChu/$PKG_NAME
     ```
   - If required to skip win platform, add:
     ```yaml
     build:
       skip: true  # win
     ```
