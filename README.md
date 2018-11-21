## OpenCV: Open Source Computer Vision Library

### Resources

* Homepage: <http://opencv.org>
* Docs: <http://docs.opencv.org/master/>
* Q&A forum: <http://answers.opencv.org>
* Issue tracking: <https://github.com/opencv/opencv/issues>

### Contributing

Please read the [contribution guidelines](https://github.com/opencv/opencv/wiki/How_to_contribute) before starting work on a pull request.

#### Summary of the guidelines:

* One pull request per issue;
* Choose the right base branch;
* Include tests and documentation;
* Clean up "oops" commits before submitting;
* Follow the [coding style guide](https://github.com/opencv/opencv/wiki/Coding_Style_Guide).

## Build for pyenv

```
mkdir build
cd build

PREFIX=`pyenv prefix`
cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX="$PREFIX" \
    -D PYTHON3_EXECUTABLE="$PREFIX"/bin/python3.6 \
    -D PYTHON3_PACKAGES_PATH="$PREFIX"/lib/python3.6/site-packages \
    -D PYTHON3_LIBRARY="$PREFIX"/lib/libpython3.6m.a \
    -D PYTHON3_INCLUDE_DIR="$PREFIX"/include/python3.6m \
    -D PYTHON3_NUMPY_INCLUDE_DIRS="$PREFIX"/lib/python3.6/site-packages/numpy/core/include \
    -D INSTALL_C_EXAMPLES=OFF \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D BUILD_EXAMPLES=ON \
    -D BUILD_opencv_python3=ON \
    -D INSTALL_NAME_DIR=${CMAKE_INSTALL_PREFIX}/lib ..

make -j8

make install
```