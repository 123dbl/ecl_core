##############################################################################
# Cmake
##############################################################################

cmake_minimum_required(VERSION 3.5)
project(ecl_statistics)

##############################################################################
# ament
##############################################################################

find_package(ament_cmake REQUIRED)
find_package(ecl_build REQUIRED)
find_package(ecl_config REQUIRED)
find_package(ecl_linear_algebra REQUIRED)
find_package(ecl_mpl REQUIRED)
find_package(ecl_type_traits REQUIRED)

##############################################################################
# Project Configuration
##############################################################################

ecl_enable_cxx14_compiler()
include_directories(include
  ${ecl_build_INCLUDE_DIRS}
  ${ecl_config_INCLUDE_DIRS}
  ${ecl_linear_algebra_INCLUDE_DIRS}
  ${ecl_mpl_INCLUDE_DIRS}
  ${ecl_type_traits_INCLUDE_DIRS}
  )

##############################################################################
# Sources
##############################################################################

add_subdirectory(include)
add_subdirectory(src)

##############################################################################
# Exports
##############################################################################

ament_export_include_directories(include)
ament_export_libraries(${PROJECT_NAME})
ament_export_dependencies(
    ecl_config
    ecl_linear_algebra
    ecl_mpl
    ecl_type_traits
)
ament_package()
