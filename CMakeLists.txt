cmake_minimum_required(VERSION 3.1)

find_package(Boost COMPONENTS unit_test_framework REQUIRED)


add_definitions(-pedantic -Wall -O2 -Wfatal-errors)
#add_definitions(-pedantic -Wall -O0 -ggdb)

set(CMAKE_CXX_STANDARD 11)

add_library(boost_arena
	obstack.cpp
)
target_link_libraries(boost_arena)


add_executable(arena_test
	arena_test.cpp
)

target_link_libraries(arena_test
	boost_arena
	"${Boost_UNIT_TEST_FRAMEWORK_LIBRARY}"
)

add_executable(arena_benchmark
	arena_benchmark.cpp
)

target_link_libraries(arena_benchmark
	boost_arena
)
