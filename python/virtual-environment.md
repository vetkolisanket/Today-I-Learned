# Virtual Environment in Python

## What is a virtual environment, why it is used?
Virtual environments in python allow different python projects to have their own isolated python environment, this is useful when say two different projects use the same library/dependency but its different version. In such cases having two different virtual environments for these two projects makes it possible to provide the correct library/dependency version to each of these projects. It is generally recommended to have separate virtual enviroments for each of your python project. That way the dependencies of each project are isolated from the system and from each other.

To install virtual environment run the following command:

```
pip install virtualenv
```

To check the version of your virtual environment or to test your installation:

```
virtualenv --version
```


## How to create one?

Use the below command:

```
virtualenv my_name
```

It is generally recommended to keep all your virtual environments at one place:

```
virtualenv ~/virts/venv-my-project-name
```

## How to activate and deactivate?

To activate a virtual environment use the below command:

```
source ~/virts/venv-my-project-name/bin/activate
```

You can install your dependencies in your virtual environment which will remain specific to that virtual environment:

```
(venv-my-project-name)$ pip install Django==1.9
```

To deactivate:

```(venv-my-project-name)$ deactivate```
