pl-brainmgz
================================

.. image:: https://travis-ci.org/FNNDSC/brainmgz.svg?branch=master
    :target: https://travis-ci.org/FNNDSC/brainmgz

.. image:: https://img.shields.io/badge/python-3.8%2B-blue.svg
    :target: https://github.com/FNNDSC/pl-brainmgz/blob/master/setup.py

.. contents:: Table of Contents


Abstract
--------

A ChRIS FS app to load FreeSurfer ``brain.mgz`` files.


Description
-----------

``brainmgz.py`` is a ChRIS FS plugin that simply delivers a payload of 25 FreeSurfer ``brain.mgz`` files to its ``/outgoing`` directory.

The primary purpose of this plugin is simply a convenient means to create the root node of a ChRIS feed tree.


Usage
-----

.. code::

    [python] brainmgz                               \
        [-h|--help]                                 \
        [--json] [--man] [--meta]                   \
        [--savejson <DIR>]                          \
        [-v|--verbosity <level>]                    \
        <inputDir> <outputDir>


Arguments
~~~~~~~~~

.. code::

    [-h] [--help]
    If specified, show help message and exit.

    [--json]
    If specified, show json representation of app and exit.

    [--man]
    If specified, print (this) man page and exit.

    [--meta]
    If specified, print plugin meta data and exit.

    [--savejson <DIR>]
    If specified, save json representation file to DIR and exit.

    [-v <level>] [--verbosity <level>]
    Verbosity level for app. Not used currently.

    [--version]
    If specified, print version number and exit.


Getting inline help is:

.. code:: bash

    docker run --rm fnndsc/pl-brainmgz brainmgz --man

Run
~~~

If running from the CLI, simply create an output directory and volume map that into the container.

.. code:: bash

    mkdir out && chmod 777 out
    docker run --rm                                         \
        -v $(pwd)/out:/outgoing                             \
        fnndsc/pl-brainmgz brainmgz                         \
        /outgoing


Development
-----------

Build the Docker container:

.. code:: bash

    docker build -t local/pl-brainmgz .



.. image:: https://raw.githubusercontent.com/FNNDSC/cookiecutter-chrisapp/master/doc/assets/badge/light.png
    :target: https://chrisstore.co
