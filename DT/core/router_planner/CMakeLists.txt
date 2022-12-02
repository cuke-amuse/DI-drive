cmake_minimum_required(VERSION 3.1)

#include (CTest)
#enable_testing()

project(router_planner_dt VERSION 1.0.0 LANGUAGES CXX)

add_executable(router_planner_dt
    ./test_rp.cpp
)

target_link_libraries(router_planner_dt PRIVATE gtest pthread) 