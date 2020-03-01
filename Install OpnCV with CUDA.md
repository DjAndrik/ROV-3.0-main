# First of all
Install required packages: 
    
    sudo apt install -y build-essential gcc g++ make
    sudo apt install -y cmake cmake-gui git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
    sudo apt install -y python-dev python-numpy python3-dev python3-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev
   
# Install Nvidia CUDA TOOLKIT
Go to this site and install: [CUDA TOOLKIT](https://developer.nvidia.com/cuda-downloads).


 # Download OpenCV source code
 Create new folder and clone source code from GitHub:
    
    cd ~ && mkdir OpenCV
    git clone https://github.com/opencv/opencv.git
    git clone https://github.com/opencv/opencv_contrib.git
 Create a temporary directory for building:
 
    mkdir build
 
 # Configure OpenCV
 Run cmake-gui:
    set full path to OpenCV source code, e.g. /home/user/OpenCV/opencv
    set full path to <cmake_build_dir>, e.g. /home/user/OpenCV/build
 
 Description of some parameters
    build type: CMAKE_BUILD_TYPE=Release\Debug
    to build with modules from opencv_contrib set OPENCV_EXTRA_MODULES_PATH to <path to opencv_contrib/modules/> e.g /home/user/OpenCV/opencv_contrib
    set BUILD_DOCS for building documents
    set BUILD_EXAMPLES to build all examples

[optional] Install with CUDA
    set WITH_CUDA, and reconfigure
    set ENABLE_FAST_MATH
    set CUDA_FAST_MATH

[optional] Building python. Set the following python parameters:

    PYTHON2(3)_EXECUTABLE = <path to python>
    PYTHON_INCLUDE_DIR = /usr/include/python<version>
    PYTHON_INCLUDE_DIR2 = /usr/include/x86_64-linux-gnu/python<version>
    PYTHON_LIBRARY = /usr/lib/x86_64-linux-gnu/libpython<version>.so
    PYTHON2(3)_NUMPY_INCLUDE_DIRS = /usr/lib/python<version>/dist-packages/numpy/core/include/

[optional] Building java.

    Unset parameter: BUILD_SHARED_LIBS
    It is useful also to unset BUILD_EXAMPLES, BUILD_TESTS, BUILD_PERF_TESTS - as they all will be statically linked with OpenCV and can take a lot of memory.

[optional] Generate pkg-config info

    Add this flag when running CMake: -DOPENCV_GENERATE_PKGCONFIG=ON
    Will generate the .pc file for pkg-config and install it.
    Useful if not using CMake in projects that use OpenCV
    Installed as opencv4, usage: pkg-config --cflags --libs opencv4

Build. From build directory execute make, it is recommended to do this in several threads

For example
    make -j7 # runs 7 jobs in parallel

After this do
    sudo make install
