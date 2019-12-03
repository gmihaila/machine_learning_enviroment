# Machine Learning Enviroment

## Python Enviroment

Compile **Python** from source

* ### Compile tcl and tk:
    
    Get: http://www.tcl.tk/software/tcltk/download.html
    
    TCL
    
    ```bash
    wget https://prdownloads.sourceforge.net/tcl/tcl8.6.10-src.tar.gz
    gunzip tcl8.6.10-src.tar.gz
    tar -xvf tcl8.6.10-src.tar
    cd tcl8.6.10/unix
    ./configure --prefix=/home/cnel711 --exec-prefix=/home/cnel711
    make
    make install
    ```
    
    TK
    
    ```bash
    wget https://prdownloads.sourceforge.net/tcl/tk8.6.10-src.tar.gz
    gunzip tk8.6.10-src.tar.gz
    tar -xvf tk8.6.10-src.tar
    cd tk8.6.10/unix/
    ./configure --prefix=/home/cnel711 --exec-prefix=/home/cnel711 --with-tcl=/home/cnel711/tcl8.5.11/unix
    make
    make install
    ```

* ### Compile OpenSSL:
    
    Get Openssl: https://www.openssl.org/source/
    
    ```bash
    wget https://www.openssl.org/source/openssl-1.1.1c.tar.gz
    gunzip openssl-1.1.1c.tar.gz
    tar -xvf openssl-1.1.1c.tar
    cd openssl-1.1.1c
    ./config --prefix=[local install]
    make
    make install
    ```
* ### Compile libffi

    Get libffi: https://sourceware.org/libffi/
    ```bash
    wget ftp://sourceware.org/pub/libffi/libffi-3.2.1.tar.gz
    gunzip libffi-3.2.1.tar.gz
    tar -xvf libffi-3.2.1.tar
    cd libffi-3.2.1
    ./configure --prefix=[local install]
    make
    make install
    ```
    

* ### Compile Python
    Get python: https://www.python.org/downloads/source/
    
    Example for **Python 3.7.4**
    ```bash
    wget https://www.python.org/ftp/python/3.7.4/Python-3.7.4.tar.xz
    tar -xvf Python-3.7.4.tar.xz
    cd Python-3.7.4
    vim Modules/Setup.dist
    ```
    search for SSL= and add path to open ssl: path/openssl/ssl
    
    Load libffi
    ```bash
    export PKG_CONFIG_PATH=path/libffi/lib/pkgconfig
    ```
    to check if libffi is set properly use:
    ```bash
    pkg-config --cflags libffi
    ```
    Should get something like 
    ```bash
    -I/path/libffi/lib/lbffi-x.x.x/include
    ```
    <br>
    Now compile Python with appropriate flags:
        
    Configure
     ```bash
    LDFLAGS=`pkg-config --libs-only-L libffi` ./configure --prefix=[local install] --with-ensurepip=install
    ```
    Make and install
    ```bash
    make
    make test
    make install
    ```
    Symbolic link so it works when calling python:
    ```bash
    ln -s python3 python
    ```



### Machine Learning Libraries

## Tensorflow Enviroment [CPU]

## Tensorflow Enviroment [GPU]

## Pytorch Enviroment [CPU + GPU]
