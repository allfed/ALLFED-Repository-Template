# ALLFED-Repository-Template
Fork this and use it as a template when you start a new project!

# Things to add
* Environments
* Project Skeleton
* Code examples

# Environment
Every ALLFED project is run in its own virtual environment. Therefore, every project needs an `environment.yml` file. The one in this repository is only an example and should not be used for any actual project. To create and organize virtual environments we use [conda](https://docs.conda.io/en/latest/miniconda.html). 


# Python Style Guide
All code written for ALLFED should follow the [PEP 8 Style Guide for Python](https://peps.python.org/pep-0008/). Especially important are:
* Keep the code well documented
* Every function needs a docstring in this form:
```
def my_function(parameter1, parameter2):
  """
  Explanation of what the function does
  
  Explanation of what the parameters contain and their type
  
  Explanation of what the return value contains and its type
  """
```
* Functions should do exactly one thing and be no longer than 20 lines
* Every function needs a test to make sure it works as intendet
  
  



# Acknowledgment
This is strongly based on the ["Good Research Code Handbook"](https://goodresearch.dev/index.html). If something here confuses you, it makes sense to read about it there. Pretty good explanations. 
