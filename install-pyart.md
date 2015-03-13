===== Instalar en Ubuntu/Debian =====

git clone https://github.com/ARM-DOE/pyart.git
cd pyart/
python setup.py build


===== Requerimientos =====

==== RSL es un paquete de TRMM ====

tar xvfz rsl-v1.47.tar.gz 
cd rsl-v1.47/
./configure 
make
sudo make install



==== Instalar netCDF ====

=== Dependencias de netCDF ===

    sudo apt-get install libhdf5-dev libhdf4-dev libnetcdf-dev

    tar xvfz netCDF4-1.1.6.tar.gz 
    cd netCDF4-1.1.6/
    sudo python setup.py install

==== Instalar Basmap ====

=== Dependencias Basemap ===

    sudo apt-get install libgeos-dev

    Crear los enlaces simbólicos si da el error:
    
    /usr/bin/ld: cannot find -lgeos

    así:

    cd /usr/lib
    sudo ln -s libgeos-3.3.3.so libgeos.so
    sudo ln -s libgeos-3.3.3.so libgeos.so1

    Ahora si, instalar basemap

    tar xvfz basemap-1.0.7.tar.gz
    cd basemap-1.0.7/
    python setup.py build
    python setup.py install


