RaspiCam and RaspiVid project

### How to build:
Create a new directory for build, then run cmake and make
```
mkdir build
cd build
cmake ..
make
```

### How to run the RaspiCam test program:
```
cd build/utils
LD_PRELOAD=/usr/lib/uv4l/uv4lext/armv6l/libuv4lext.so ./camera_test
```

### How to run the RaspiVid test program:
```
cd build/utils
LD_PRELOAD=/usr/lib/uv4l/uv4lext/armv6l/libuv4lext.so ./video_test
```

### How to build and run the example program:
```
# Copy library files from when the project was built
cd examples
cp ../build/src/lib* ./

# Compile example program
g++ -L/usr/lib/uv4l/uv4lext/armv6l -I ../src/ -L ./ -lraspicam -luv4lext -Wl,-rpath,'/usr/lib/uv4l/uv4lext/armv6l' `pkg-config --cflags opencv` `pkg-config --libs opencv` -o FindContours FindContours.cpp

# Run example program
LD_PRELOAD=/usr/lib/uv4l/uv4lext/armv6l/libuv4lext.so ./FindContours;
```

### Possible Problems:
If you are using Memory Mapping (RaspiVid::METHOD_MMAP) then when you run the program you must be sure to specify LD_PRELOAD before you execute.