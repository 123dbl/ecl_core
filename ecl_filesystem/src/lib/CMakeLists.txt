###############################################################################
# SOURCES
###############################################################################

# Note, macro magic stops us compiling objects for the wrong implementations below
SET(SOURCES 
    realpath.cpp
)
###############################################################################
# Install
###############################################################################

add_library(${PROJECT_NAME} ${SOURCES})
target_link_libraries(${PROJECT_NAME} 
  ${ecl_build_LIBRARIES}
  ${ecl_config_LIBRARIES}
  ${ecl_errors_LIBRARIES}
  ${ECL_PLATFORM_FILESYSTEM_LIBRARIES})
install(TARGETS ${PROJECT_NAME}
   RUNTIME DESTINATION bin
   ARCHIVE DESTINATION lib
   LIBRARY DESTINATION lib
   PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
)

