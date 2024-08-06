# this can be much lower
cmake_minimum_required(VERSION 3.17)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++17")

project(monte_carlo)

add_executable(monte_carlo)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++17")

#Copy CSV files with data to binary dir
file(GLOB MY_INPUT_CSV_FILES *.csv)
file(COPY ${MY_INPUT_CSV_FILES} DESTINATION ${CMAKE_CURRENT_BINARY_DIR})


file(GLOB_RECURSE ALL_FILES 
        "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp" 
        "${CMAKE_CURRENT_SOURCE_DIR}/include/*.h")

target_sources(monte_carlo
        PRIVATE
                ${ALL_FILES}
)

target_include_directories(monte_carlo
        PRIVATE
                ${CMAKE_CURRENT_SOURCE_DIR}/include
)

