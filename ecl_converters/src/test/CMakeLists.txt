###############################################################################
# Google Tests Macro
###############################################################################

macro(ecl_converters_add_gtest test_name)
  ament_add_gtest(ecl_test_${test_name} ${test_name}.cpp)
  if(TARGET ecl_test_${test_name})
    target_link_libraries(ecl_test_${test_name}
      ${ecl_concepts_INCLUDE_DIRS}
      ${ecl_config_LIBRARIES}
      ${ecl_errors_LIBRARIES}
      ${ecl_exceptions_LIBRARIES}
      ${ecl_mpl_LIBRARIES}
      ${ecl_type_traits_LIBRARIES}
    )
  endif()
endmacro()

###############################################################################
# Google Tests
###############################################################################

ecl_converters_add_gtest(byte_array_converters)
ecl_converters_add_gtest(converters)
