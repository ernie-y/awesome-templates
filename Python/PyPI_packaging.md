# [PyPI Python Packaging](https://towardsdatascience.com/how-to-publish-a-python-package-to-pypi-7be9dd5d6dcd)

## Generate the distribution archives on local machine.
Now that the code for the python package is almost complete, you can start building the distribution archives. Archives are compressed files that help your package to be deployed across multiple platforms and also make it platform independent. In order to generate the distribution archives, run the following command from your terminal.

```python
python -m pip install –-user –-upgrade setuptools wheel
```
This will upgrade your setuptools library on your machine to use the latest version. After this, you need to run the following command from the root directory of your package to generate the distribution files.

```python
python setup.py sdist bdist_wheel
```
Once you run the above command, you can see that the distribution packages will be delivered under the directories — build and dist, that are newly created as below. In addition to that, you can also see that the egg file information has been updated in the project source code as well.


## Install the package on local machine.
Now that we have our distribution files ready, we can go ahead and try installing and importing the package to test if it works fine. In order to install the package on your local machine, run the following command from the root directory.
```python
pip install -e .
```
As you can see in the figure above, in the first step we install the package locally using the command and once it is installed, we start the python shell and import it. Then we call the package method and it prints the message to the terminal.

## Publish the package to the [TestPyPi](https://test.pypi.org/)
Once the package is installed on local and works fine, it is now ready to be shipped to the TestPyPi repository. This is a test repository for all python packages to test and see if all code works fine and there are no issues within the package code. This keeps it isolated from the official PyPi repository and makes sure that only thorough tested packages are deployed to production.

Navigate to https://test.pypi.org/ and Register yourself as an user. Once you are registered, open your terminal and run the following command. This will install a package called “twine” on your machine that will help ship the python package to the repositories.
```python
python -m pip install — user — upgrade twine
```

You can read the official documentation about [packaging python applications](https://packaging.python.org/en/latest/tutorials/packaging-projects/) and also about [twine](https://twine.readthedocs.io/en/latest/) here. After the twine package is installed, run the following command to ship the code to TestPyPi first. When you run the command, you will be asked to provide the same credentials using which you have registered your account in the previous step.

```python
python -m twine upload — repository testpypi dist/*
```

## Publish the package to the [PyPi](https://pypi.org/) repository
```python
python -m twine upload dist/*
```
