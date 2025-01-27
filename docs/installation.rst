Installation
============

Python Version
--------------

Python >= 3.7 

Install with Pip
----------------

.. code-block:: bash 

	pip install picaso

Note with a pip install you will need to download the `Reference Folder from Github <https://github.com/natashabatalha/picaso/tree/master/reference>`_ (explained below). This can simply be done by downloading a zip of the ``PICASO`` code from Github (which does not require git setup). 

Install with Git
----------------

.. code-block:: bash 

	git clone https://github.com/natashabatalha/picaso.git
	cd picaso
	python setup.py install 

Download and Link Reference Documentation
-----------------------------------------

1) With pip, download the `Reference Folder from Github <https://github.com/natashabatalha/picaso/tree/master/reference>`_. You should already this if you did a Git clone. **Make sure that your reference folder matches the version number of ``PICASO``**. Check the version number in the file ``reference/version.md``. 

2) Download the `Resampled Opacity File from Zenodo <https://doi.org/10.5281/zenodo.3759675>`_. Place in the `Opacities reference Folder you downloaded from Github <https://github.com/natashabatalha/picaso/tree/master/reference>`_ (see below in step 3)

3) Now you can create an environment variable:


.. code-block:: bash

	vi ~/.bash_profle

Add add this line:

.. code-block:: bash

	export picaso_refdata="/path/to/picaso/reference/"

Should look something like this 

.. code-block:: bash

	cd /path/to/picaso/reference/
	ls
	base_cases chemistry config.json evolution opacities version.md

Your opacities folder shown above should include the file ``opacities.db`` `file downloaded from zenodo <https://doi.org/10.5281/zenodo.3759675>`_. This is mostly a matter of preference, as PICASO allows you to point to an opacity directory. Personally, I like to store something with the reference data so that I don't have to constantly specify a folder path when running the code. 

Download and Link Pysynphot Stellar Data
----------------------------------------

In order to get stellar spectra you will have to download the stellar spectra here from PySynphot: 

1) PICASO uses the `Pysynphot package <https://pysynphot.readthedocs.io/en/latest/appendixa.html>`_ which has several download options for stellar spectra. The Defulat for ``PICASO`` is Castelli-Kurucz Atlas: `ck04models <https://archive.stsci.edu/hlsps/reference-atlases/cdbs/grid/ck04models/>`_. 

You can download them by doing this: 

.. code-block:: bash

	wget http://ssb.stsci.edu/trds/tarfiles/synphot3.tar.gz

When you untar this you should get a directory structure that looks like this ``<path>/grp/redcat/trds/grid/ck04models``. Some other people have reported a directory structure that looks like this ``<path>/grp/hst/cdbs/grid/ck04models``. **The full directory structure does not matter**. Only the last portion ``grid/ck04models``. You will need to create an enviornment variable that points to where ``grid/`` is located. See below.


2) Create environment variable via bash 

.. code-block:: bash

	vi ~/.bash_profle

Add add this line:

.. code-block:: bash

	export PYSYN_CDBS="<your_path>/grp/redcat/trds"

Then always make sure to source your bash profile after you make changes. 

.. code-block:: bash

	source ~/.bash_profile

Now you should be able to check the path:

.. code-block:: bash

	cd $PYSYN_CDBS
	ls
	grid

Where the folder ``grid/`` contains whatever ``pysynphot`` data files you have downloaded (e.g. a folder called ``ck04models/``). 

.. note::

	1. STScI serves these files in a few different places, with a few different file structures. **PySynphot only cares that the environment variable points to a path with a folder called `grid`. So do not worry if `grp/hst/cdbs` appears different.** 

