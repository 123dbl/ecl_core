##############################################################################
# Cmake
##############################################################################

cmake_minimum_required(VERSION 3.5)
project(ecl_linear_algebra)

##############################################################################
# ament
##############################################################################

find_package(ament_cmake REQUIRED)
find_package(ecl_build REQUIRED)
find_package(ecl_eigen REQUIRED)
find_package(ecl_exceptions REQUIRED)
find_package(ecl_formatters REQUIRED)
find_package(ecl_math REQUIRED)

find_package(sophus REQUIRED)

##############################################################################
# Project Configuration
##############################################################################

ecl_enable_cxx14_compiler()

include_directories(include
  ${ecl_build_INCLUDE_DIRS}
  ${ecl_eigen_INCLUDE_DIRS}
  ${ecl_exceptions_INCLUDE_DIRS}
  ${ecl_formatters_INCLUDE_DIRS}
  ${ecl_math_INCLUDE_DIRS}
  ${sophus_INCLUDE_DIRS}
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
    ecl_eigen
    ecl_exceptions
    ecl_formatters
    ecl_math
    sophus
)
ament_package()
