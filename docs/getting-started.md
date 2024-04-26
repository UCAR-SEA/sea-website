# How to Use this Template Repository? 🛠️

**Estimated time to completion: 30 minutes 🕗**

In this page, you will find information on how to start your own documentation page project using this template. This guide will walk you through the steps of getting started with such a template, including initial setup, customization, and deployment.

## Step 1: Create a New Repository Using This Template

1. Click the **"Use this template"** button on the top right of [this repository's GitHub page](https://github.com/NCAR/NCAR_mkdocs_template) to create a new repository using this template. Please see the image below for reference:


	![Use this template](./assets/use-this-template.png)


2. Once you click on "Use this Template", Github opens a new page. Here give your repository a name. Make sure the project is “Public”, rather than “Private”. Then click "Create Repository" button. This will create a new repository under your account with the same files and structure as this repository.

In general, the repository is organized into the following sections:

```
mkdocs.yml        # The MkDocs configuration file.
themes/           # Customized theme files.
    ...           # (sourced from https://github.com/NCAR/NCAR_mkdocs_material_themes)
docs/
    index.md      # The documentation homepage.
    ...           # Other markdown pages, images and other docs files.
conda.yaml        # A conda environment definition with the Python dependencies to build the project.
.readthedocs.yml  # The configuration file for readthedocs hosting.
```

We will go over each of these files and directories in the next steps.

## Step 2: Modify your Repository to include your content:

Once the repository is created, you can clone it to your local machine and start working on it. You can add new markdown files, images, and other documentation files to the `docs` directory. You can also customize the `mkdocs.yml` file to change the site name, navigation, and other settings.

For example, edit the `mkdocs.yml` file to customize the site name, navigation, and other settings. For example, you can change site name, site description, and author:

```
# ------------------------------------
# -------- Project Information -------
# ------------------------------------
site_name: NCAR MkDocs Template
site_description: A template for creating NCAR mkdocs
repo_url: https://github.com/NCAR/NCAR_mkdocs_template/
site_url: https://ncar-mkdocs-template.readthedocs.io/en/latest/
site_author: CISL CSG (Consulting Services Group)
```

You can also customize the pages you want to show by editing the `nav` section of the `mkdocs.yml` file. The following example shows how to add a simple page or a nested section with new pages to the navigation:

```
# ------------------------------------
# -------- Navigation ----------------
# ------------------------------------
nav:
  - Home: index.md

  # New Example Page
  - Example Page: example-page.md


  # New Section with Subpages
  - Example Section 1:
    - example-section-1/index.md
	  - Example Sub-page 1: example-section-1/example-subpage-1.md
	  - Example Sub-page 2: example-section-1/example-subpage-2.md

```
!!! info
    The markdown files in the `docs` directory are used to generate the documentation. You can add new markdown files, images, and other documentation files to the `docs` directory.

Please see the [MkDocs documentation](https://www.mkdocs.org/user-guide/configuration/) for more information on customizing the `mkdocs.yml` navigation and other settings.

## Step 3: Building the Documentation Locally

If you want to build the documentation locally to see the changes you've made, you can do so by following these steps:

### Create a `conda` Environment
To build the documentation locally and preview it, you'll need to install certain dependencies. Although this step is optional, we strongly recommend it.

The example provided here creates a new  `conda` environment named `mkdocs` from the provided `conda.yaml` file.

  ```bash
  conda env create -f conda.yaml
  conda activate mkdocs
  ```

Please note that you only need to create the `conda` environment once. Once the environment is created, you can activate it using `conda activate mkdocs` whenever you want to build the documentation locally in the future.

### Preview Documentation Locally
You can preview your documentation locally to make sure that your changes do not introduce any errors. With MkDocs, you can preview your changes by running `mkdocs serve` in your terminal. This starts a local server where you can preview your work.

  ```
  mkdocs serve
  ```

!!! note
      `mkdocs serve --strict` will enable strict mode and treat warnings as errors. This is useful to ensure that your changes do not introduce any issues such as new pages that does not exist.  Occasionally you may want to omit the `--strict` flag, for example when adding new pages that have not yet been committed through `git`.


Please note that while building and previewing the documentation locally, is optional, it is a good practice to do so to ensure that your changes do not introduce any errors.

## Step 4: Deploying the Documentation

Once you have made your changes and are ready to deploy the documentation to ReadTheDocs page, you can do so by following these steps: 


1. Go to [ReadTheDocs.org](https://readthedocs.org/) website and sign in with your Github account. While you can use other methods to sign , we recommend using Github as it makes it easier to import your repository from Github.

2. Once logged in, click on "Import a Project" and select this new repository from the list of your repositories. Please note that for deploying the docs to ReadTheDocs, you need to have a `readthedocs.yml` file in the root of your repository. This file is already included in this template repository, so you don't need to create one.

    ![Import a Project](./assets/import_project.png)

    !!! warning
		  Please note that you need to have your repository set to public in order to deploy the documentation to ReadTheDocs as ReadTheDocs does not support private repositories with free accounts.

3. For ReadTheDocs to build the documentation successfully using this template, you need to add an environment variable to your ReadTheDocs project settings. Here we used [ReadTheDocs  user-defined environment variables ](https://docs.readthedocs.io/en/stable/environment-variables.html) to distinguish the `DEPLOY_TARGET` at build time (`NCAR_primary`, `iframe`, etc...) in case you want to deploy multiple versions of the documentation for embedding in ARC or other sites.

    For this go to the "Admin" page on ReadTheDocs and click on "Environment Variables".
    
    ![Nav to env variable](./assets/admin_page.png)

    
     Next, add a new environment variable with the name `DEPLOY_TARGET` and the value `NCAR_primary` or `arc_iframe` depending on the target you want to deploy. `NCAR_Primary` is the default value and is used to deploy the primary documentation site. `arc_iframe` is used to deploy the documentation with a customized theme to be easily embedded in ARC website. **For the first deployment, use `NCAR_primary` as the value for `DEPLOY_TARGET`.**


    ![Env Variable](./assets/env_var.png)

    !!! tip
        Make sure you mark the "Expose this environment variable in PR builds?" checkbox if you want to preview your documentation from a pull request. 
    

    Once you have added the environment variable, ReadTheDocs will automatically build the documentation and host it at a unique URL. You can access the documentation at this URL and share it with others.

    !!! note
	    If you are interested in creating another page for embedding the docs in ARC, you can do so by creating a new ReadTheDocs project and adding the `DEPLOY_TARGET` environment variable with the value `arc_iframe`. This will create a new version of the documentation with a customized theme but without headers and footers to be easily embedded in [ARC](https://arc.ucar.edu/). For example, see this [ARC iframed style docs](https://arc.ucar.edu/docs).

4. **Optional:** If you are interested in ReadTheDocs to preview your documentation from a pull request, you can do so by going on the ReadTheDocs.org and your project. Then go to the "Admin" page and click on "Advanced Settings" and mark the "Pull Request Preview" feature. Please see the screenshot below. This will allow ReadTheDocs to build a preview of your documentation and add it to the pull request. This allows you to preview your changes before they are merged into the main branch.

    ![Enable PR Build](./assets/enable_pr_build.png)


5. **Optional:** If you are interested, you can copy the docs badge from the ReadTheDocs page and add it to your repository's README.md file. This badge will show the documentation status and link to the documentation page. You can find the badge on the ReadTheDocs page of your project. Please see the image below for reference:

    ![ReadTheDocs Badge](./assets/badge.png)

If you have any questions regarding this workflow, please feel free to reach out to [CISL Consulting Services Group](mailto:csg@ucar.edu) for assistance.


## Additional Resources
* [Markdown Cheatsheet](https://www.markdownguide.org/cheat-sheet/)
* [mkdocs documentation](https://www.mkdocs.org/user-guide/configuration/)
* [Material for MkDocs documentation](https://squidfunk.github.io/mkdocs-material/)
* [ReadTheDocs documentation](https://docs.readthedocs.io/en/stable/)
* [NCAR HPC Documentation](https://ncar-hpc-docs.readthedocs.io/en/latest/)
