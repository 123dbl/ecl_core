##############################################################################
# Cmake
##############################################################################

cmake_minimum_required(VERSION 3.5)
project(ecl_eigen)

##############################################################################
# ament
##############################################################################

find_package(ament_cmake REQUIRED)

##############################################################################
# Internal vs External Eigen
##############################################################################

# Internal eigen logic is quite broken since ament, surgically removed for now
# Leaving the infrastructure in place though, in case we should need to make
# use of it again

find_package(Eigen3)
if(EIGEN3_FOUND)
    set(ECL_EIGEN_IS_EXTERNAL 1 CACHE BOOL "Using the system's eigen3 implementation.")
    # On trusty, it sets EIGEN3_INCLUDE_DIR but not EIGEN3_INCLUDE_DIRS (xenial is fine), so help it
    if(NOT EIGEN3_INCLUDE_DIRS)
      set(EIGEN3_INCLUDE_DIRS ${EIGEN3_INCLUDE_DIR})
    endif()
else()
    message(STATUS "Eigen not found...using ecl's internal eigen.")
    set(ECL_EIGEN_IS_EXTERNAL 0 CACHE BOOL "Using the system's eigen3 implementation.")
endif()

##############################################################################
# Project Configuration
##############################################################################

file(MAKE_DIRECTORY ${PROJECT_BINARY_DIR}/include)

configure_file(
  ${CMAKE_CURRENT_SOURCE_DIR}/include/ecl/eigen.hpp.in
  ${PROJECT_BINARY_DIR}/include/ecl/eigen.hpp
)

install(
  FILES ${PROJECT_BINARY_DIR}/include/ecl/eigen.hpp
  DESTINATION include/ecl
)

##############################################################################
# Sources
##############################################################################

add_subdirectory(include)
add_subdirectory(license)

##############################################################################
# Export
##############################################################################

ament_export_include_directories(include/ecl)
ament_export_dependencies(
    Eigen3
)
ament_package()
