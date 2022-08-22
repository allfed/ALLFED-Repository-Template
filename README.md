# ALLFED-Repository-Template
Use this as template when you start a new project


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
* This repository is automatically set up with Github Actions/[Lint Action](https://github.com/marketplace/actions/lint-action) that will format your code using black and check for problems with flake8 ([without E203, W503](https://black.readthedocs.io/en/stable/faq.html#why-are-flake8-s-e203-and-w503-violated)). If either of them fails, you will not be able to merge your files unless you fix it. If this creates problem you cannot solve contact: florian@allfed.info


To make this easier you can use linter (auto-formatter) that change your code to be formatted in PEP 8 when you safe it. E.g. [here for Spyder](https://stackoverflow.com/questions/51463223/how-to-use-pep8-module-using-spyder) or [VS Code](https://code.visualstudio.com/docs/python/linting). 

## Testing
We want to create reliable code. This means, as much of the code needs to be automatically tested, to make sure that everything runs as intended. Therefore, every possible function should have some kind of `assert` that tests if it works. We use pytest [pytest](https://docs.pytest.org/en/7.1.x/) as our main test suit. All tests that you put in the tests folder in here are automatically run every time you push code. You can read more about testing [here](https://goodresearch.dev/testing.html). To adapt the testing.yml to your repository you just have to adapt the requirements in requirements.txt. Everything else should work on its own. 

## Documenting
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
* (if the project gets very big) an automated documentation via [Gitub Actions]()
* Create a [visual representation](https://goodresearch.dev/_images/pcbi.1007358.g002.PNG_L.png) of how the different files interact with each other

   
## Project Skeleton
This repository already has the folder structure we use for repositories. Every folder has an additional readme, to tell you what needs to go in there. 

## Making the repository a pip installable Python package
For some repositories it makes sense to make them installable via pip (e.g. a model we want to share easily). In this case you can use the explanation [here](https://goodresearch.dev/setup.html). This repository already contains a setup.py that can be used for that. 

## Environment
Every ALLFED project is run in its own virtual environment. Therefore, every project needs an `environment.yml` file. The one in this repository is only an example and should not be used for any actual project. To create and organize virtual environments we use [conda](https://docs.conda.io/en/latest/miniconda.html). 

## Requirements
Every ALLFED project needs a requirements file that specifies what packages are needed to run the project. You can find an example file in the repository. 

## License
ALLFED publishes its code in Open Access. For this we use the [**Apache 2.0 License**](https://www.planetcrust.com/what-does-apache-2-0-license-mean). This license allows very free use of the code, but makes sure that ALLFED cannot be sued if something goes wrong with the code. The license template in this repository needs to be adapted when a new project is created. 

## Gitignore
The [.gitignore file](https://git-scm.com/docs/gitignore) is the default one for Python. Make sure you change it when using another programming language. 

## Further reading/Misc
* [Best Practices for Scientific Computing](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001745)
* [General course to get to know the Python skills needed to the work at ALLFED](https://github.com/florianjehn/python-for-environmental-science)
* We are using [Github Copilot](https://github.com/features/copilot) to write faster and cleaner code. If you would also like to have a license contact finance@allfed.info or florian@allfed.info

## Acknowledgment
This is strongly based on the ["Good Research Code Handbook"](https://goodresearch.dev/index.html). If something here confuses you, it makes sense to read about it there. Pretty good explanations. 
