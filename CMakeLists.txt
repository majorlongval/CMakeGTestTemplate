cmake_minimum_required(VERSION 3.13.4)

# Setting the project name 
project(TEMPLATE)

add_executable(${PROJECT_NAME} main.cpp)

# Adding the subdir for the lib so it finds the CMake in the subdir
add_subdirectory(my_lib)

# Adding the subdir for gtest
add_subdirectory(external/googletest)

# Tells Cmake to add the items in the dir to the include path 
target_include_directories(${PROJECT_NAME} 
    PUBLIC my_lib 
    PUBLIC external/googletest/googletest/include
    PUBLIC external/googletest/googlemock/include
)

# Specifies the paths in which the linker should search for librairies
# When linking for a specific target 
target_link_directories(${PROJECT_NAME} 
    PRIVATE my_lib
    PRIVATE external/googletest/googletest/src
    PRIVATE external/googletest/googlemock/src
)

# Links the mylib library to the ${PROJECT_NAME} target
target_link_libraries(${PROJECT_NAME} mylib gtest gtest_main gmock gmock_main)