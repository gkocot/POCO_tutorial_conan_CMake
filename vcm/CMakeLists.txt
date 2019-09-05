cmake_minimum_required(VERSION 3.12)

set(PROJECT_NAME "vcm")
project(${PROJECT_NAME})

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

add_executable(
    ${PROJECT_NAME}
    vcm/vcm.cpp
)

target_link_libraries(
    ${PROJECT_NAME}
    ${CONAN_LIBS}
)

add_dependencies(
    ${PROJECT_NAME}
    copy-conf
)

add_custom_target(
    copy-conf
    COMMAND ${CMAKE_COMMAND} -E copy ${CMAKE_SOURCE_DIR}/conf/vcm.properties ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}
    COMMAND ${CMAKE_COMMAND} -E copy ${CMAKE_SOURCE_DIR}/conf/any.pem ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}
    COMMAND ${CMAKE_COMMAND} -E copy ${CMAKE_SOURCE_DIR}/conf/rootcert.pem ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}
)