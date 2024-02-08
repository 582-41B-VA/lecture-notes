# Python packaging

## Installing packages

Python allows you to download and install *distribution packages* such
as libraries and frameworks using the `pip` command. The `pip` program
is included with most modern versions of Python. To make sure `pip` is
available to you, execute the following command:

```sh
pip --version
```

If the `pip` command returns an error, refer to the [official
documentation][pip installation] for troubleshooting.

To install a distribution package, execute the command `pip install
package-name`. By default, pip will fetch packages from [Python Package
Index][] (also know as PyPI), a repository of software for the Python
programming language where anyone can upload packages.

[pip installation]: https://pip.pypa.io/en/stable/getting-started/#ensure-you-have-a-working-pip
[Python Package Index]: https://pypi.org

## Virtual environment

It is good practice to install distribution packages inside projects
that need them.

Imagine you have a project that needs version 1 of a package, but
another that requires version 2. How can you work on both at the same?
The answer is to use *virtual environments*, each with their own
independent set of Python packages.

To create a virtual environment, run the `venv` module followed by the
name of the directory in which you want to put packages:

```sh
python -m venv .venv
```

Then, activate the virtual environment by executing the "activate" shell
script inside the "bin" subdirectory:

```sh
source .venv/bin/activate
```

Once the virtual environment is activated, you should see its name in
parentheses (venv) in your prompt. If you close the current shell, do
not forget to reactivate the virtual environment once you resume
working the project.

## Resources

- [Python packaging user guide](https://packaging.python.org/en/latest/)