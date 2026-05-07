cmake_minimum_required(VERSION 3.4)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

option(BUILD_EXAMPLES "Build examples" OFF)

project(formatter)

add_subdirectory(formatter_lib)
add_subdirectory(formatter_ex)
add_subdirectory(solver_lib)

if(BUILD_EXAMPLES)
    add_subdirectory(hello_world_application)
    add_subdirectory(solver_application)
endif()

install(TARGETS formatter formatter_ex hello_world solver
    EXPORT formatter-config
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
    RUNTIME DESTINATION bin
)

install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/ DESTINATION include)
install(EXPORT formatter-config DESTINATION cmake)
install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/ DESTINATION include)
install(EXPORT print-config DESTINATION cmake)
