cmake_minimum_required(VERSION 3.10)

# Set the project name
project(path_tracer)

# Specify the C++ standard
#set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Compiler options
if (CMAKE_CXX_COMPILER_ID STREQUAL "Clang")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -w")
elseif (CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -w")
endif()

# Add include directories
include_directories(Libraries/include/)
include_directories(Libraries/include/imgui)

# Add the source files
file(GLOB SOURCES 
    "./Libraries/include/imgui/*.cpp"
    "./source/glad.c"
    "./source/*.cpp"
)

# Define the executable
add_executable(path_tracer ${SOURCES})

# Link libraries
target_link_libraries(path_tracer glfw)

# Compiler definitions
target_compile_definitions(path_tracer PRIVATE LIBCXX_ENABLE_INCOMPLETE_FEATURES)
