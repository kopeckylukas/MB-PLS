Multiblock Partial Least Squares Package
========================================


.. image:: https://img.shields.io/pypi/l/mbpls.svg
    :target: https://pypi.python.org/pypi/mbpls/
    :alt: License
.. image:: https://readthedocs.org/projects/mbpls/badge/?version=latest
    :target: https://mbpls.readthedocs.io/en/latest/?badge=latest
    :alt: Documentation Status
.. image:: http://joss.theoj.org/papers/10.21105/joss.01190/status.svg
   :target: https://doi.org/10.21105/joss.01190
   :alt: JOSS Paper DOI

   .. note::

      This is a newly maintained version of the package, based on the original
      MBPLS software originally developed by Andreas Baum and Laurent Vermue 
      (homepabe: https://github.com/DTUComputeStatisticsAndDataAnalysis/MBPLS/).

      This maintained version has been updated to be compatible with Python 3.8 and later, and modern
      version of the dependencies. The original version of the package is no longer maintained, 
      and users are encouraged to use this updated version for their work.

      To cite this package, plase use the original publication by Baum et al. (2019) as described below 
      or refer to the GitHub repository for the most recent updates and contributions.

      Lukas Kopecky (l.kopecky22@imperial.ac.uk), April 2026.

An easy to use Python package for (Multiblock) Partial Least Squares
prediction modelling of univariate or multivariate outcomes. Four state
of the art algorithms have been implemented and optimized for robust
performance on large data matrices. The package has been designed to be
able to handle missing data, such that application is straight forward
using the commonly known Scikit-learn API and its model selection
toolbox.

The documentation is available at https://mbpls.readthedocs.io
and elaborate (real-world) Jupyter Notebook examples can be found at
https://github.com/kopeckylukas/MB-PLS/tree/master/examples

This package can be cited using the following reference. 

*Baum et al., (2019). Multiblock PLS: Block dependent prediction modeling for Python. Journal of Open Source Software, 4(34), 1190*



Installation
------------

-  | Install the package for Python3 using the following command. Some
     dependencies might require an upgrade (scikit-learn, numpy and
     scipy).
   | ``$ pip install mbpls``

-  | Now you can import the MBPLS class by typing
   | ``from mbpls.mbpls import MBPLS``

Quick Start
-----------

Use the mbpls package for Partial Least Squares (PLS) prediction modeling
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

   import numpy as np
   from mbpls.mbpls import MBPLS

   num_samples = 40
   num_features = 200

   # Generate random data matrix X
   x = np.random.rand(num_samples, num_features)

   # Generate random reference vector y
   y = np.random.rand(num_samples,1)

   # Establish prediction model using 2 latent variables (components)
   pls = MBPLS(n_components=2)
   pls.fit(x,y)
   y_pred = pls.predict(x)

The mbpls package for Multiblock Partial Least Squares (MB-PLS) prediction modeling
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

   import numpy as np
   from mbpls.mbpls import MBPLS

   num_samples = 40
   num_features_x1 = 200
   num_features_x2 = 250

   # Generate two random data matrices X1 and X2 (two blocks)
   x1 = np.random.rand(num_samples, num_features_x1)
   x2 = np.random.rand(num_samples, num_features_x2)

   # Generate random reference vector y
   y = np.random.rand(num_samples, 1)

   # Establish prediction model using 3 latent variables (components)
   mbpls = MBPLS(n_components=3)
   mbpls.fit([x1, x2],y)
   y_pred = mbpls.predict([x1, x2])

   # Use built-in plot method for exploratory analysis of multiblock pls models
   mbpls.plot(num_components=3)
