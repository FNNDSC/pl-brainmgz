.. code:: console

         _               _
        | |             (_)
        | |__  _ __ __ _ _ _ __  _ __ ___   __ _ ____
        | '_ \| '__/ _` | | '_ \| '_ ` _ \ / _` |_  /
        | |_) | | | (_| | | | | | | | | | | (_| |/ /
        |_.__/|_|  \__,_|_|_| |_|_| |_| |_|\__, /___|
                                            __/ |
                                           |___/

        


pl-brainmgz
================================

.. image:: https://img.shields.io/docker/v/fnndsc/pl-brainmgz?sort=semver
    :target: https://hub.docker.com/r/fnndsc/pl-brainmgz

.. image:: https://img.shields.io/github/license/fnndsc/pl-brainmgz
    :target: https://github.com/FNNDSC/pl-brainmgz/blob/master/LICENSE

.. image:: https://github.com/FNNDSC/pl-brainmgz/workflows/ci/badge.svg
    :target: https://github.com/FNNDSC/pl-brainmgz/actions

.. contents:: Table of Contents


Abstract
--------

A ChRIS FS app to deliver embedded FreeSurfer ``brain.mgz`` and ``aparc.*``  files to its output directory. These files are made available as part of the Human Connectome Project.


Description
-----------

``brainmgz`` is a ChRIS FS plugin that simply delivers a payload of 25 FreeSurfer ``brain.mgz`` and ``aparc.*`` segmented volume files to its ``/outgoing`` directory.

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
