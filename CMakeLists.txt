cmake_minimum_required(VERSION 3.14)
project(oop1lab LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)

include(FetchContent)

set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)

FetchContent_Declare(
    googletest
    URL https://github.com/google/googletest/archive/refs/heads/main.zip
)
FetchContent_MakeAvailable(googletest)

enable_testing()

add_executable(oop1lab
    main.cpp
    src/replacinfunc.cpp
)
target_include_directories(oop1lab PRIVATE include)

add_executable(oop1lab_tests
    tests/tests.cpp
    src/replacinfunc.cpp
)

target_include_directories(oop1lab_tests PRIVATE include)

target_link_libraries(oop1lab_tests gtest_main)

include(GoogleTest)
gtest_discover_tests(oop1lab_tests)