cmake_minimum_required(VERSION 2.8.7)
project(clustering)


catkin_package(
  INCLUDE_DIRS include
  LIBRARIES ${PROJECT_NAME}
)

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")

# show additional files in qtcreator
execute_process(COMMAND find ${PROJECT_SOURCE_DIR} -type f
  OUTPUT_VARIABLE FILES_STRING)
string(REPLACE "\n" ";" FILES_LIST ${FILES_STRING})
add_custom_target(additional_files_${PROJECT_NAME} SOURCES
  ${FILES_LIST}
  ${PROJECT_SOURCE_DIR}/../README.md
)

include_directories(include
  ${catkin_INCLUDE_DIRS}
)

add_library(${PROJECT_NAME}
  src/OpticsClustering.cpp
)

target_link_libraries(${PROJECT_NAME}
  ${catkin_LIBRARIES}
)


