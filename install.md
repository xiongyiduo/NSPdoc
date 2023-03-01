## Installation requirements

- g++ version is greater than 4.8

## Compile and install

1. upgrade g++

    If the g++ version is less than 4.8, you need to upgrade the g++ firstly. Here take gcc-4.9.3 as an example:

    - root user
    ```
    wget http://mirror.hust.edu.cn/gnu/gcc/gcc-4.9.3/gcc-4.9.3.tar.gz
    tar xvzf gcc-4.9.3.tar.gz
    cd gcc-4.9.3
    ./contrib/download_prerequisites
    mkdir build
    cd build
    ../configure --enable-checking=release --enable-languages=c,c++ --disable-multilib
    make -j4
    sudo make install
    ```

    - ordinary user
    ```
    wget http://mirror.hust.edu.cn/gnu/gcc/gcc-4.9.3/gcc-4.9.3.tar.gz
    tar xvzf gcc-4.9.3.tar.gz
    cd gcc-4.9.3
    ./contrib/download_prerequisites
    mkdir build
    cd build
    ../configure --enable-checking=release --enable-languages=c,c++ --disable-multilib --prefix=<PATH/TO/INSTALL/GCC>
    make -j4
    sudo make install
    ```

2. download nsp
    You can download NSP from our <a herf=http://biophy.hust.edu.cn/new/resources/3dRNA>webserver</a> or you can input the command below on the command line:
    ```
    wget http://biophy.hust.edu.cn/new/downloads/NSP.tar.gz
    tar -zxvf NSP.tar.gz
    ```

3. Set the environment.
    ```
    export NSP=<PATH/TO/NSP/Lib/>
    ```

