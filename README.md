# ALLFED-Repository-Template

If this is the first time you want to use this template, please go through the [Github training](https://github.com/allfed/Github-Training-Repository/blob/main/README.md) first. This will give you the neccesary background knowledge to understand what is happening here. 

## How to use this template
Use this as template when you start a new project by clicking "Use this template" in the top right.

Then follow all the descriptions below. 

## ALLFED Python Style Guide
All code written for ALLFED should follow the [PEP 8 Style Guide for Python](https://peps.python.org/pep-0008/). Especially important are:
* Keep the code well documented
* Every function needs a docstring in this form:
```
def count_line(f, line):
    """
    Counts the number of times a line occurs. Case-sensitive.

    Arguments:
        f (file): the file to scan
        line (str): the line to count

    Returns:
        int: the number of times the line occurs.
    """
```
* Write [decoupled code](https://goodresearch.dev/decoupled.html), e.g. Functions should do exactly one thing and be as short as possible
* Naming conventions:
  - Snake case for variables and module: variable_name, my_module.py
  - Camel case for class name: MyClass
  - Camel case with spaces for jupyter notebook: Analyze Brain Data.ipynb
* Delete dead code! Don't outcomment code you don't use anymore, but delete it instead. If you need to find it again, that's what we have git for. 
* Use Jupyter Notebooks only for explanations and visualization. The actual programming should be happening in `.py` files. 
* This repository is automatically set up with Github Actions/[Lint Action](https://github.com/marketplace/actions/lint-action) that will format your code using black and check for problems with flake8 ([without E203](https://github.com/psf/black/blob/06ccb88bf2bd35a4dc5d591bb296b5b299d07323/docs/guides/using_black_with_other_tools.md#flake8)). If either of them fails, you will not be able to merge your files unless you fix it. If this creates problem you cannot solve contact: florian@allfed.info
* You can deactivate the branch protection that makes sure that only correct and styled code can be merged, but it is not recommended. 


To make this easier you can use linter (auto-formatter) that change your code to be formatted in PEP 8 when you safe it. E.g. [here for Spyder](https://stackoverflow.com/questions/51463223/how-to-use-pep8-module-using-spyder) or [VS Code](https://code.visualstudio.com/docs/python/linting). 

## Testing
We want to create reliable code. This means, as much of the code needs to be automatically tested, to make sure that everything runs as intended. Therefore, every reasonable function should have some kind of `assert` that tests if it works. We use pytest [pytest](https://docs.pytest.org/en/7.1.x/) as our main test suit. All tests that you put in the tests folder in here are automatically run every time you push code. You can read more about testing [here](https://goodresearch.dev/testing.html). To adapt the testing.yml to your repository you just have to adapt the requirements in requirements.txt. Everything else should work on its own. You can find an example of how a test file should look like in the tests folder. Once you go the testing set up, also make sure to add the testing badge to the readme of your repository. Simply change the URL to your repository in this badge:

![Testing](https://github.com/allfed/allfed-repository-template/actions/workflows/testing.yml/badge.svg)

You don't have to test every possible function. Just make sure that those are tested where you are doing custom analysis. 

## Documenting in small projects
Documenting your code is only one part of the documentation we want to create. Every larger repository needs:
* a readme file that explains what the repository is for and how it is organized, which should contain:
    - A one-sentence description of your project
    - A longer description of your project
    - Installation instructions
    - General orientation to the codebase and usage instructions
    - Links to papers
    - Links to extended docs
    - License

* a tutorial Jupyter Notebook to explain how the repository is supposed to be used


## Documenting in big projects
All the things for the small projects, but also:
* An automated documentation via Gitub Actions. This is already set up in this repository. Is uses the code from [this post](https://towardsdatascience.com/easily-automate-and-never-touch-your-documentation-again-a98c91ce1b95) and combines it with [this one](https://blog.elmah.io/deploying-a-mkdocs-documentation-site-with-github-actions/). It also is setup that it will only look for python files in the src folder. So, make sure that everything is in there (you can changes this behavior in the main function of `automate_mkdocs.py`). To get it running do the following
    * Change the names in `mkgendocs.yml` and `mkdocs.yml` so they fit your repository
    * go to Settings --> Pages 
    * select deploy from a branch as source
    * select gh-pages as branch at root (for this option to pop up the `docs.yml` file has to have run succesfully at least once, this should happen when you push anything in your repository)
    * The end result will look something [like this](https://florianjehn.github.io/Seaweed-Growth-Model/)
    * The automated documentation part is still a bit wip, if you run into problems contact florian@allfed.info
* Create a [visual representation](https://goodresearch.dev/_images/pcbi.1007358.g002.PNG_L.png) of how the different files interact with each other

## Issues
Every time you come across a problem that you do not plan to fix in the next day, please open an issue in the repository to make sure that it does not get lost. This also allows you to assign tasks to other coders on the team. For a short intro to issues, see [here](https://www.youtube.com/watch?v=TKJ4RdhyB5Y).

## Making the repository citable
All ALLFED repositories should be citable by release. For this we use [Zenodo](https://zenodo.org/). This has to be activated by an Admin (so either Florian or Morgan). Once you have a manuscript where you need to cite the repository let them know and they will activate it. This will also create a doi badge, which should be included in the readme, like this:

---


[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.6865646.svg)](https://doi.org/10.5281/zenodo.6865646)


---

## ALLFED Plotting Style
All plots created for ALLFED should look and feel the same. You can activate the ALLFED style by simply starting your code with:

`plt.style.use("https://raw.githubusercontent.com/allfed/ALLFED-matplotlib-style-sheet/main/ALLFED.mplstyle")`

If you need to create your plots in ALLFED style, while being offline just download the file and change the path to local. 

### Map Projection

For published maps we use the [Winkel Tripel projection](https://en.wikipedia.org/wiki/Winkel_tripel_projection). You can use it by reprojecting the CRS of your data on geopandas to `+proj=wintri`. The function in the example below can be used to include a border on your map, and modify the ALLFED plotting style to make sense for a map plot.


```python
# Add border to map, remove gridlines and ticks (after activating ALLFED style)
def plot_winkel_tripel_map(ax): 
    border_geojson = gpd.read_file('https://raw.githubusercontent.com/ALLFED/ALLFED-map-border/main/border.geojson')
    border_geojson.plot(ax=ax, edgecolor='black', linewidth=0.1, facecolor='none')
    ax.set_axis_off()

world = gpd.read_file(gpd.datasets.get_path('naturalearth_lowres')) # Example world dataset
world = world.to_crs('+proj=wintri') # Change projection to Winkel Tripel

ax = world.plot() # Plot the map
plot_winkel_tripel_map(ax) # Modify style and add border
plt.show()
```

The result should look like this:

<img src="https://raw.githubusercontent.com/JuanesLamilla/winkel-tripel-border/main/winkel_tripel_map.png" width=50% height=50%>

Important note: The Winkel Tripel projection is a compromise projection used purely for visuals. It is not equal-area, conformal, or equidistant. This means that the areas, angles, and distances are not preserved. We use this projection to make our maps as easy to read as possible, but if you need to do any calculations on the map, you need to use a different appropriate projection to get the correct results. To learn more about map projections with geopandas, see [here](https://geopandas.org/en/v0.14.0/docs/user_guide/projections.html).
   
## Project Skeleton
This repository already has the folder structure we use for repositories. Every folder has an additional readme, to tell you what needs to go in there.

## Making the repository a pip installable Python package
For some repositories it makes sense to make them installable via pip (e.g. a model we want to share easily). In this case you can use the explanation [here](https://goodresearch.dev/setup.html). This repository already contains a setup.py that can be used for that. If you want to install it to your local environment just run `pip install -e .` while being in the folder that contains setup.py.

## Environment
Every ALLFED project is run in its own virtual environment. Therefore, every project needs an `environment.yml` file. The one in this repository is only an example and should not be used for any actual project. To create and organize virtual environments we use [conda](https://docs.conda.io/en/latest/miniconda.html). 

Please make sure to include version numbers in your `environment.yml`. Otherwise it will be really annoying to get it to run again in the future. 

## Requirements
Every ALLFED project needs a requirements file that specifies what packages are needed to run the project. You can find an example file in the repository. If you use a lot of packages you can use [pipreqg](https://allfed.github.io/Seaweed-Growth-Model/) to find them all.  

## License
ALLFED publishes its code in Open Access. For this we use the [**Apache 2.0 License**](https://www.planetcrust.com/what-does-apache-2-0-license-mean). This license allows very free use of the code, but makes sure that ALLFED cannot be sued if something goes wrong with the code. The license template in this repository needs to be adapted when a new project is created. You can include the following license badge in your readme:

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

## Gitignore
The [.gitignore file](https://git-scm.com/docs/gitignore) is the default one for Python. Make sure you change it when using another programming language. 

## Further reading/Misc
* [Best Practices for Scientific Computing](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001745)
* [General course to get to know the Python skills needed to the work at ALLFED](https://github.com/florianjehn/python-for-environmental-science)
* We are using [Github Copilot](https://github.com/features/copilot) to write faster and cleaner code. If you would also like to have a license contact finance@allfed.info

## Acknowledgment
This is strongly based on the ["Good Research Code Handbook"](https://goodresearch.dev/index.html). If something here confuses you, it makes sense to read about it there. Pretty good explanations. 
