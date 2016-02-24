## Build for host system (linux x86)

    mkdir build && cd build && cmake .. && make


## Build for ARM board

    mkdir build && cd build
    CC=arm-none-linux-gnueabi-gcc CXX=arm-none-linux-gnueabi-g++ cmake ..
    make
