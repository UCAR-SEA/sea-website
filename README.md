# UCAR Software Engineering Assembly Website

[![Documentation Status](https://readthedocs.org/projects/ncar-mkdocs-template/badge/?version=latest)](https://ncar-mkdocs-template.readthedocs.io/en/latest/?badge=latest)

This repository generates the UCAR SEA website from markdown files using the [MkDocs](https://www.mkdocs.org/) platform along with the customized [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) theme. The theme files have been customized to align with NCAR branding and colors and is available in the [NCAR_mkdocs_material_themes](https://github.com/NCAR/NCAR_mkdocs_material_themes).


## How to contribute updates/changes

1. Fork this repository
2. Clone it on your local computer and ensure the theme submodule is cloned too:
```
git clone git@github.com:<user>/sea-website.git
cd sea-website
git submodule init
git submodule update
```
3. Install [micromamba](https://mamba.readthedocs.io/en/latest/installation/micromamba-installation.html) (or miniconda) *if you do not have it already*
4. Create a mkdocs environment for testing the website locally:
```
conda env create -n mkdocs conda.yaml
```
5. Activate the environment by running `micromamba activate mkdocs`
6. Create and check out a new update branch using `git checkout -b branch-name`
7. Make modifications to pages contained in `docs/` subdirectory
8. If you add content that requires menu navigation, make sure to edit the `nav:` section of **mkdocs.yaml** too
9. Preview your changes by running `mkdocs serve` and opening the localhost link in your browser
10. Once satisfied :smile_cat: with how your changes appear, add and commit modifications
11. Push your branch to your fork on Github using `git push -u origin branch-name`
12. Create the pull request on Github

## License

This material is licensed under Creative Commons Attribution ShareAlike 4.0 ([CC-BY-SA-4.0](https://creativecommons.org/licenses/by-sa/4.0/)).  You are free to:

- **Share** — copy and redistribute the material in any medium or format for any purpose, even commercially.

- **Adapt** — remix, transform, and build upon the material for any purpose, even commercially.


Under the following terms:

- **Attribution** - You must give appropriate credit , provide a link to the license, and indicate if changes were made . You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.

- **ShareAlike** - If you remix, transform, or build upon the material, you must distribute your contributions under the same license as the original.
No additional restrictions - You may not apply legal terms or technological measures that legally restrict others from doing anything the license permits.

See [here](https://creativecommons.org/licenses/by-sa/4.0/legalcode.en) for full details.
