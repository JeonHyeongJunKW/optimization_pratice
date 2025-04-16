cmake_minimum_required(VERSION 3.0)
project(robust_curve_fitting LANGUAGES CXX)

if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

find_package(absl REQUIRED)
find_package(Ceres REQUIRED)
find_package(Eigen3 3.1.0 REQUIRED NO_MODULE)
################################################################################
# Build
################################################################################
set(CMAKE_BUILD_TYPE Release)
message("Build type is Release")

include_directories(
  # ${PROJECT_SOURCE_DIR}/include
  ${EIGEN3_INCLUDE_DIR}
)

add_executable(
  ${PROJECT_NAME}
  ${PROJECT_SOURCE_DIR}/src/main.cpp)

target_link_libraries(
  ${PROJECT_NAME}
  absl::log_initialize
  absl::log
  Ceres::ceres
  # realsense2::realsense2
)
