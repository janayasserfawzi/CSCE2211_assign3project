add_subdirectory(lib)
include_directories(lib/googletest/include)
include_directories(lib/googlemock/include)
add_executable(Google_Tests_run Testcases.cpp)
target_link_libraries(Google_Tests_run
        PRIVATE
        Code_library
        gtest
        gtest_main
)
