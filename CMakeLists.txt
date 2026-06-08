cmake_minimum_required(VERSION 3.4)

project(lab06)

set(PRINT_VERSION_MAJOR 0)
set(PRINT_VERSION_MINOR 1)
set(PRINT_VERSION_PATCH 0)
set(PRINT_VERSION_TWEAK 0)

set(PRINT_VERSION
  ${PRINT_VERSION_MAJOR}.${PRINT_VERSION_MINOR}.${PRINT_VERSION_PATCH}.${PRINT_VERSION_TWEAK})

set(PRINT_VERSION_STRING "v${PRINT_VERSION}")

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_subdirectory(formatter_lib)
add_subdirectory(formatter_ex)
add_subdirectory(solver_lib)
add_subdirectory(hello_world_application)
add_subdirectory(solver_application)

install(TARGETS solver
        RUNTIME DESTINATION bin)

install(TARGETS solver_lib formatter_lib formatter_ex
        ARCHIVE DESTINATION lib
        LIBRARY DESTINATION lib)

install(FILES solver_lib/solver.h
              formatter_lib/formatter.h
              formatter_ex/formatter_ex.h
        DESTINATION include)
include(CPackConfig.cmake)
