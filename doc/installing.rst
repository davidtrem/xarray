.. _installing:

Installation
============

Required dependencies
---------------------

- Python 2.7 [1]_, 3.5, or 3.6
- `numpy <http://www.numpy.org/>`__ (1.12 or later)
- `pandas <http://pandas.pydata.org/>`__ (0.19.2 or later)

Optional dependencies
---------------------

For netCDF and IO
~~~~~~~~~~~~~~~~~

- `netCDF4 <https://github.com/Unidata/netcdf4-python>`__: recommended if you
  want to use xarray for reading or writing netCDF files
- `scipy <http://scipy.org/>`__: used as a fallback for reading/writing netCDF3
- `pydap <http://www.pydap.org/>`__: used as a fallback for accessing OPeNDAP
- `h5netcdf <https://github.com/shoyer/h5netcdf>`__: an alternative library for
  reading and writing netCDF4 files that does not use the netCDF-C libraries
- `pynio <https://www.pyngl.ucar.edu/Nio.shtml>`__: for reading GRIB and other
  geoscience specific file formats
- `zarr <http://zarr.readthedocs.io/>`__: for chunked, compressed, N-dimensional arrays.
- `cftime <https://unidata.github.io/cftime>`__: recommended if you
  want to encode/decode datetimes for non-standard calendars or dates before
  year 1678 or after year 2262.
- `PseudoNetCDF <http://github.com/barronh/pseudonetcdf/>`__: recommended
  for accessing CAMx, GEOS-Chem (bpch), NOAA ARL files, ICARTT files
  (ffi1001) and many other.
- `rasterio <https://github.com/mapbox/rasterio>`__: for reading GeoTiffs and
  other gridded raster datasets.
- `iris <https://github.com/scitools/iris>`__: for conversion to and from iris'
  Cube objects.

For accelerating xarray
~~~~~~~~~~~~~~~~~~~~~~~

- `scipy <http://scipy.org/>`__: necessary to enable the interpolation features for xarray objects
- `bottleneck <https://github.com/kwgoodman/bottleneck>`__: speeds up
  NaN-skipping and rolling window aggregations by a large factor
  (1.1 or later)
- `cyordereddict <https://github.com/shoyer/cyordereddict>`__: speeds up most
  internal operations with xarray data structures (for python versions < 3.5)

For parallel computing
~~~~~~~~~~~~~~~~~~~~~~

- `dask.array <http://dask.pydata.org>`__ (0.16 or later): required for
  :ref:`dask`.

For plotting
~~~~~~~~~~~~

- `matplotlib <http://matplotlib.org/>`__: required for :ref:`plotting`
  (1.5 or later)
- `cartopy <http://scitools.org.uk/cartopy/>`__: recommended for
  :ref:`plot-maps`
- `seaborn <https://stanford.edu/~mwaskom/software/seaborn/>`__: for better
  color palettes


Instructions
------------

xarray itself is a pure Python package, but its dependencies are not. The
easiest way to get everything installed is to use conda_. To install xarray
with its recommended dependencies using the conda command line tool::

    $ conda install xarray dask netCDF4 bottleneck

.. _conda: http://conda.io/

We recommend using the community maintained `conda-forge <https://conda-forge.github.io/>`__ channel if you need difficult\-to\-build dependencies such as cartopy, pynio or PseudoNetCDF::

    $ conda install -c conda-forge xarray cartopy pynio pseudonetcdf

New releases may also appear in conda-forge before being updated in the default
channel.

If you don't use conda, be sure you have the required dependencies (numpy and
pandas) installed first. Then, install xarray with pip::

    $ pip install xarray

Testing
-------

To run the test suite after installing xarray, first install (via pypi or conda)

- `py.test <https://pytest.org>`__: Simple unit testing library
- `mock <https://pypi.python.org/pypi/mock>`__: additional testing library required for python version 2

and run
``py.test --pyargs xarray``.


Performance Monitoring
~~~~~~~~~~~~~~~~~~~~~~

A fixed-point performance monitoring of (a part of) our codes can be seen on
`this page <https://tomaugspurger.github.io/asv-collection/xarray/>`__.

To run these benchmark tests in a local machine, first install

- `airspeed-velocity <https://asv.readthedocs.io/en/latest/>`__: a tool for benchmarking Python packages over their lifetime.

and run
``asv run  # this will install some conda environments in ./.asv/envs``

.. [1] Xarray plans to drop support for python 2.7 at the end of 2018. This
   means that new releases of xarray published after this date will only be
   installable on python 3+ environments, but older versions of xarray will
   always be available to python 2.7 users. For more information see the
   following references:

      - `Xarray Github issue discussing dropping Python 2 <https://github.com/pydata/xarray/issues/1829>`__
      - `Python 3 Statement <http://www.python3statement.org/>`__
      - `Tips on porting to Python 3 <https://docs.python.org/3/howto/pyporting.html>`__
