##############################################################################
# Cmake
##############################################################################

cmake_minimum_required(VERSION 3.5)
project(ecl_sigslots)

##############################################################################
# Find Packages
##############################################################################

find_package(ament_cmake REQUIRED)
find_package(ecl_build REQUIRED)
find_package(ecl_config REQUIRED)
find_package(ecl_threads REQUIRED)

##############################################################################
# Project Configuration
##############################################################################

ecl_enable_cxx14_compiler()

include_directories(include ${ecl_config_INCLUDE_DIRS})

##############################################################################
# Sources
##############################################################################

add_subdirectory(include)
add_subdirectory(src)

##############################################################################
# Exports
##############################################################################

ament_export_include_directories(include)
ament_export_dependencies(
    ecl_config
    ecl_threads
)
ament_package()
