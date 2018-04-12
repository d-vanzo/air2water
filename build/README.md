# How to build air2water on Linux environment

## Setup the building environment
* required packages
    * fortran compiler (e.g. gfortran)
    * cmake package

On Ubuntu OS the required packages can be easily installed via terminal with

~~~bash
sudo apt-get install gfortran cmake
~~~

## Build the program

Open the terminal and navigate into `air2water/build/` subfolder and run

~~~bash
cmake ../src/
make
~~~

*NOTE: if you want to check compiling options, use `make VERBOSE=1` instead.*

Move the created executable to the main folder (`air2water`) and let it run!