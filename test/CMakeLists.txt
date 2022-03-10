set(TestTarget ${CMAKE_PROJECT_NAME}_tst)


add_executable(${TestTarget} main.cpp otherTestFile.cpp)


# Tells Cmake to add the items in the dir to the include path 
target_include_directories(${TestTarget}
    PUBLIC ../include
    PUBLIC ../my_lib 
    PUBLIC ../external/googletest/googletest/include
    PUBLIC ../external/googletest/googlemock/include
)

# Specifies the paths in which the linker should search for librairies
# When linking for a specific target 
target_link_directories(${TestTarget}
    PRIVATE ../my_lib
    PRIVATE ../external/googletest/googletest/src
    PRIVATE ../external/googletest/googlemock/src
)

# Links the mylib library to the ${TestTarget} target
target_link_libraries(${TestTarget} mylib gtest gtest_main gmock gmock_main)