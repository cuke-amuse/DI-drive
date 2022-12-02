cmake_minimum_required(VERSION 3.1)

project(test_entry VERSION 1.0.0 LANGUAGES CXX)

option(ADS_ENABLE_TEST "enable test for ads" ON)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror -Wextra")

IF (${ADS_ENABLE_TEST})
    include (CTest)
    enable_testing()
endif()

add_executable(test_entry)

file(GLOB all_test CONFIGURE_DEPENDS
    ./*.cpp
    ./*.cc
)

target_sources(test_entry PRIVATE
    ${all_test}
)

target_include_directories(test_entry PRIVATE
    googletest/include
) 

target_link_libraries(test_entry PRIVATE 
    gtest
    gmock
    pthread
) 

add_test(NAME behavior_planner_dt COMMAND behavior_planner_dt)
add_test(NAME router_planner_dt COMMAND router_planner_dt)

if (BUILD_TESTING)
    add_subdirectory(core)
endif()