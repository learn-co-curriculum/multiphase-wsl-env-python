# Windows WSL2 Python Installation

**Note**: Depending on where you are in the curriculum and when you started the
program, you may already have installed `pyenv`, Python, and `pipenv`. If so,
you are free to skip this lesson. Before continuing, however, we recommend that
you verify that everything is set up correctly by completing the steps in the
"Verify and Troubleshoot your WLS2 Environment Setup" lesson.

**Important**: We do not install Python using the installer from python.org in
our curriculum. If you have installed Python using this tool, you should
uninstall it before installing this version of Python.

Currently the curriculum for this course is compatible with Python 3.8.

## Installing pyenv

Before installing Python, we need to install the Python version manager pyenv.
This is similar to the nvm tool we used to install Node.JS, except it controls
which versions of Python we use on our system.

To install pyenv, we use the `pyenv-installer`.

Per the instructions on the `pyenv-installer` website, we start by running the
following command in your Ubuntu terminal:

```console
$ curl https://pyenv.run | bash
```

[pyenv-installer]: https://github.com/pyenv/pyenv-installer

Unlike nvm, pyenv does not automatically add its startup lines to your shell
startup file. The shell startup file enables you to interact with your programs via the Ubuntu terminal. Thus, if you don't update this file, when you try to use pyenv, you will receive the message `bash: command not found: pyenv`.

The file that you have to update will depend on which shell you are running. You can check which shell you have from your terminal by running the command:

```console
$ echo $SHELL
```

When you set up WSL, the default shell is `/bin/bash`, which means the file we need to update is the `.bashrc` file.

To open the `.bashrc` file with VSCode, run the following command:

```console
$ code ~/.bashrc
```

Inside of Visual Studio Code, scroll to the bottom of the file and add the following lines:

```text
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
```

**Note:** After you add this code to your startup file, you will need to save this file. In the top tool bar you can click **file** > **save** or you can enable auto save by clicking on **file** > **auto save**. This automatically saves every change you make to any file from here on out.

Leave your Visual Studio Code application open, because we are going to have to update your shell startup file again later. To get your Ubuntu terminal to recognize the changes made to your startup file, restart your terminal.

---

## Installing Dependencies on Windows and Ubuntu

For Windows and Ubuntu users you will need to install some extra dependencies
for Python.

First run this command to update your apt repositories:

```console
$ sudo apt update
```

Next, run this command to install the packages listed on the pyenv:

```console
$ sudo apt-get install -y build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev python3-openssl git
```

## Installing Python

Run the following command to install Python (you'll notice pyenv makes us put in
the exact version instead of being able to just say 3.8 or 3):

```console
$ pyenv install 3.8.13
```

After some time this should complete without any errors. It could take a while
since you are compiling Python from source code.

Once this is finished we also need to tell pyenv this is our default version of
Python using this command:

```console
$ pyenv global 3.8.13
```

Ensure that these changes take effect by closing your terminal and opening a new
one.

### Checking Your Work

You can verify that you have the correct version of Python installed by typing:

```console
$ python --version
$ python3 --version
```

Both of these commands should show 3.8.13

---

## Installing Pipenv

Another piece of software we will use in class is Pipenv. We will learn more
about what Pipenv is later; for now, go ahead and install it:

```console
$ pip install pipenv
```

After you have installed pipenv, modify your shell startup file (`.bashrc`) to add an export line.

**Note:** If you closed out VSCode, refer back to the instructions above on how to re-open the shell startup file.

The export line should go somewhere
after the `eval "$(pyenv init --path)"`. To create a new line, click on the end of the last line of the file and hit **Enter** on your keyboard. Then, on the newly created line paste in the code below:

```text
export PIPENV_VENV_IN_PROJECT=1
```

Congratulations! If you've completed all these steps you are ready to code in
Python!
