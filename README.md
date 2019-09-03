# POCO_tutorial_conan_CMake
conan remote add bintray-pocoproject https://api.bintray.com/conan/pocoproject/conan
conan remote add bintray-conan-community https://api.bintray.com/conan/conan-community/conan
cd md5 && mkdir build && cd build
conan install .. --settings compiler="Visual Studio" --settings compiler.version=16 --build=missing
cmake .. -G "Visual Studio 16 2019"
cmake --build . --config Release
