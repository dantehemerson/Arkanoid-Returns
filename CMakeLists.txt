cmake_minimum_required(VERSION 3.10)

project(ArkanoidReturns)

# Set C++ standard to C++11
set(CMAKE_CXX_STANDARD 11)

# Set the path to the Allegro 5 include directory
set(ALLEGRO5_INCLUDE_DIRS "/usr/local/include/allegro5")

# Add the source files
file(GLOB_RECURSE SOURCES "src/*.cpp")

# Add the header files
file(GLOB_RECURSE HEADERS "src/*.hpp")

# Specify the path to main.cpp (assuming it's in the root folder)
set(MAIN_SOURCE "main.cpp")

# Create the executable
add_executable(${PROJECT_NAME} ${MAIN_SOURCE} ${SOURCES} ${HEADERS})

# Include the Allegro 5 directory for header files
target_include_directories(${PROJECT_NAME} PRIVATE ${ALLEGRO5_INCLUDE_DIRS})

# Link Allegro 5 library (you might not need this line)
target_link_libraries(${PROJECT_NAME} PRIVATE
    allegro
    allegro_color
    allegro_font
    allegro_ttf
    allegro_primitives
    allegro_image
    allegro_audio
    allegro_acodec
)

# Specify any other dependencies if needed.

# Optionally, set compiler flags (e.g., optimization flags)
# set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2")

# Optionally, enable testing if you have unit tests.
# enable_testing()
# add_subdirectory(tests)

# Set the output directory for the executable
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)