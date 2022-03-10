cmake_minimum_required(VERSION 3.13.4)

# Setting the project name 
project(TEMPLATE)

add_executable(${PROJECT_NAME} main.cpp)

# Adding the subdir for the lib so it finds the CMake in the subdir
add_subdirectory(my_lib)

# Tells Cmake to add the items in the dir to the include path 
target_include_directories(${PROJECT_NAME} PUBLIC my_lib)

# Specifies the paths in which the linker should search for librairies
# When linking for a specific target 
target_link_directories(${PROJECT_NAME} PRIVATE my_lib)

# Links the mylib library to the ${PROJECT_NAME} target
target_link_libraries(${PROJECT_NAME} mylib)