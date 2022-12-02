cmake_minimum_required(VERSION 3.1)

#include (CTest)
#enable_testing()

project(behavior_planner_dt VERSION 1.0.0 LANGUAGES CXX)

add_executable(behavior_planner_dt
    ./test_bp.cpp
)

target_link_libraries(behavior_planner_dt PRIVATE gtest pthread) 