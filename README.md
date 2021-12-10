# pyenv-howto

Notes for myself because i always forget the commands.

After installation of pyenv the following lines need adding to the .zshrc file.

``` bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.zshrc
```

## pyenv

To list and then install a Python version.

``` bash
pyenv install -l | grep 3.10
  3.10.0
  3.10-dev
  3.10.1
  mambaforge-4.10.3-10
  miniconda-3.10.1
  miniconda3-3.10.1
  miniforge3-4.10.3-10

pyenv install 3.10.1
```

Entering the command ``pyenv versions`` will show you all versions of Python you currently have installed on your computer. To set a particular version to be your default global version, simply enter the following command.

```bash
pyenv global 3.9.1
```

You can also set a specific Python version to be used in a particular directory by navigating into that directory and then running the following command

```bash
pyenv local 3.8.1
```

Or, you can simply set the version of Python to be used in the current Shell, by entering the following command.

```bash
pyenv shell 3.8.1
```

## virtualenvs

``` bash
mkdir new_python_project
cd new_python_project

pyenv local 3.9.1
```

To create the virtual environment, enter the command below. pyenv virtualenv is the actual command to create the environment. The version number aligns to the Python version you just set as the local version for the environment, and the final section is the name of the virtual environment. My personal preference is to prefix the name with ‘venv’, and then align the name of the virtual environment to the name of the directory it relates to.

``` bash
pyenv virtualenv 3.9.1 venv_python_project
```

The final step is to set the local python version for the directory as the virtual environment.

```bash
pyenv local venv_python_project
```

When you want to work within the virtual environment you need to activate it. Once activated, the specified version of Python will be used and any libraries you install will be contained within the environment. It is important to remember to de-activate the virtual environment once you are finished working within it in order to return to your global environment. Activating and de-activating the environment is achieved with the following commands.

``` bash
pyenv activate venv_python_project
pyenv deactivate
```

To enable auto-activation and de-activation of the virtual environment as you navigate in and out of the associated directory, simply enter the following command in the Terminal to update the .zshrc file with the required information.

```bash
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zshrc
```
