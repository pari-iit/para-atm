# para-atm

## Introduction

para-atm is a Python package that provides tools for analysis of the national air transportation system.  The project stems from the Prognostic Analysis and Reliability Assessment Laboratory (PARA) at Arizona State University.

## Installation

In short, the steps are:
- Install Python 3
- From the `src` directory, run: `python setup.py develop`

The following sections provide further details.

### Install Python

The first step is to install Python 3 on the system.

#### Ubuntu Linux

On Ubuntu 18, this can be done using:

```
sudo apt install python3
```

#### Windows

There are different ways to install Python on Windows.  One approach is to use the Anaconda distribution.  In particular, the "miniconda" installation provides a minimal install, to which further packages can be added as necessary: https://docs.conda.io/en/latest/miniconda.html.  With Anaconda on Windows, it is common to use the default settings that do not add Python to the system `PATH` environment variable, in which case all Python commands are then done within the special command prompt provided by Anaconda.

### Virtual environments

Although not strictly necessary, it is recommended to create a Python virtual environment for para-atm.  This way, all packages that are installed by para-atm are isolated and will not interfere with packages that may be needed for other projects.

#### Virtual environment on Linux

These steps should apply to any Linux distribution.  We will install the virtual environment within a directory named `venv` under the home directory, and the virtual environment will be named `para-atm`.  However, any name and location for the virtual environment may be used.

``` shell
python3 -m venv ~/venv/para-atm
```

The above command creates the new virtual environment.  To activate the virtual environment, run:

``` shell
source ~/venv/para-atm/bin/activate
```
Upon activation, the command prompt will change to show the name of the virtual environment.  The above command can be added to the `~/.bashrc` file to automatically activate the virtual environment each time a new terminal is started.  To deactivate the virtual environment, type `deactivate`.

#### Virtual environment on Windows using Anaconda

Although the above approach can be used on Windows as well (see https://docs.python.org/3.8/library/venv.html for Windows-specific information), Anaconda provides functions that make virtual environments more convenient.  From the Anaconda prompt, use:

``` shell
conda create --name para-atm python=3.7
```

The virtual environment can then be activated directly, with no need to specify the path:

``` shell
conda activate para-atm
```

See https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html for more information about working with virtual environments in Anaconda.

### Install para-atm Python package

Installation is handled via the `setup.py` script in the `src` directory.  If using a virtual environment, activate the appropriate virtual environment as described above.  Then navigate to the `src` directory and run the following command:

```
python setup.py develop
```

The `develop` command is similar to `install`, but instead of copying files into the installation directory, it creates a link to the source files.  This way, there is no need to reinstall when changes are made to para-atm.

If the installation is not being performed within a virtual environment, the following command is recommended:

``` shell
python setup.py develop --user
```
The `--user` flag ensures that the dependencies installed by para-atm do not interfere with system-wide Python packages installed via the package manager (i.e., `apt install`).

On Ubuntu 18, if the installation is not performed within a virtual environment, it will be necessary to replace the `python` command with `python3`.  This is because by default, `python` refers to `python2` on this system.


### Install NATS (optional)

Installation of the NATS (National Airspace Trajectory-Prediction System) software is optional.  Refer to the NATS documentation for installation information.

On Ubuntu Linux, the following commands install dependencies needed by NATS 1.7:

``` shell
sudo apt install default-jdk
sudo apt install libcurl4-gnutls-dev
sudo apt install libxml2-dev
```

## Testing

To test the para-atm installation, run the following command from the base directory:

```
python -m unittest
```

## Usage

The para-atm package may be used from within Python via `import paraatm`, or through the command-line interface provided by the `para-atm` command.  For help with the command-line interface, run:

```
para-atm -h
```

If para-atm was installed within a virtual environment, make sure that environment is activated.

## Documentation

The documentation is written using [Sphinx](https://www.sphinx-doc.org).  It is not yet hosted online.  In the meantime, the HTML documentation can be created locally using these steps:
- Install sphinx (`sudo apt install python3-sphinx` on Ubuntu Linux)
- From the `docs` directory, run `make html`
- Open `_build/html/index.html` in a web browser

## Contributors

The project has been developed under the guidance of ULI PI Dr. Yongming Liu, with student contributors 
as follows:

Hari Iyer,
PARA-ATM Founder & (Former)Lead Software Engineer,
hari.iyer@asu.edu.

Yutian Pang,
PARA-ATM Research Associate,
yutian.pang@asu.edu.
