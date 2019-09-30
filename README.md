# POCO_tutorial_conan_CMake
conan remote add bintray-pocoproject https://api.bintray.com/conan/pocoproject/conan
conan remote add bintray-conan-community https://api.bintray.com/conan/conan-community/conan

# Relese
cd md5 && mkdir build && cd build
conan install .. --settings compiler="Visual Studio" --settings compiler.version=16 --build=missing
cmake .. -G "Visual Studio 16 2019"
cmake --build . --config Release

# Debug
cd md5 && mkdir build_debug && cd build_debug
conan install .. --settings compiler="Visual Studio" --settings compiler.version=16 --build=missing --settings build_type=Debug
cmake .. -G "Visual Studio 16 2019"
cmake --build . --config Debug

openssl req -x509 -config openssl.cnf -set_serial 1 -nodes -days 36500 -newkey rsa:2048 -keyout any.pem -out rootcert.pem -subj "/CN=*"
type rootcert.pem >> any.pem
