add_executable(${PROJECT_NAME} main.cpp)

# Tells Cmake to add the items in the dir to the include path 
target_include_directories(${PROJECT_NAME} 
    PUBLIC include
    PUBLIC ../my_lib 
)

# Specifies the paths in which the linker should search for librairies
# When linking for a specific target 
target_link_directories(${PROJECT_NAME} 
    PRIVATE ../my_lib
)

# Links the mylib library to the ${PROJECT_NAME} target
target_link_libraries(${PROJECT_NAME} mylib)