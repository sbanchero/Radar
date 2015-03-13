
Instalar en Ubuntu/Debian
=========================

Antes de esto ver los requerimientos en PyART https://github.com/ARM-DOE/pyart y los requerimientos ad-hoc acá.

    git clone https://github.com/ARM-DOE/pyart.git
    cd pyart/
    python setup.py build


Requerimientos ad-hoc!
======================

RSL es un paquete de TRMM
-------------------------

Descargarlo desde http://trmm-fc.gsfc.nasa.gov/trmm_gv/software/rsl/

    tar xvfz rsl-v1.47.tar.gz 
    cd rsl-v1.47/
    ./configure 
    make
    sudo make install



Instalar netCDF
---------------

Dependencias de netCDF:

Debian:
        
    sudo apt-get install libhdf5-dev libhdf4-dev libnetcdf-dev

Ubuntu:

    sudo apt-get install libhdf4-dev libnetcdf-dev libhdf5-serial-dev

    Descargar el hdf5 desde http://www.hdfgroup.org/ftp/HDF5/current/src/    

        ./configure 
        make 
        sudo make install
    
    
Descargar el netCDF desde https://pypi.python.org/pypi/netCDF4

    tar xvfz netCDF4-1.1.6.tar.gz 
    cd netCDF4-1.1.6/
    sudo python setup.py install


Instalar Basmap
---------------

Dependencias Basemap:

    sudo apt-get install libgeos-dev

Crear los enlaces simbólicos si da el error:
    
    /usr/bin/ld: cannot find -lgeos

así:

    cd /usr/lib
    sudo ln -s libgeos-3.3.3.so libgeos.so
    sudo ln -s libgeos-3.3.3.so libgeos.so1

Ahora si, instalar basemap:

Debian:

    tar xvfz basemap-1.0.7.tar.gz
    cd basemap-1.0.7/
    python setup.py build
    python setup.py install

Ubuntu:

    sudo apt-get install python-mpltoolkits.basemap

Posibles errores
================

    >>> import pyart
    /usr/lib/pymodules/python2.7/mpl_toolkits/__init__.py:2: UserWarning: Module dap was already imported from None, but /usr/lib/python2.7/dist-packages is being added to sys.path
      __import__('pkg_resources').declare_namespace(__name__)

Se arregla editando: 

    sudo geany /usr/lib/python2.7/dist-packages/dap-2.2.6.7.egg-info/namespace_packages.txt
    
    agregar dap en primera linea
