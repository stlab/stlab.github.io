cmake_minimum_required( VERSION 3.2 )
set( CMAKE_CONFIGURATION_TYPES "Debug;Release" CACHE STRING "Supported configuration types" FORCE )

project( stlab_examples LANGUAGES C CXX )

file( GLOB_RECURSE examples RELATIVE ${CMAKE_CURRENT_SOURCE_DIR}/libraries "libraries/*.cpp" )
add_subdirectory( stlab )

enable_testing()
foreach( path IN LISTS examples )
  string( FIND "${path}" "." target REVERSE )
  string( SUBSTRING "${path}" 0 "${target}" target )
  string( REPLACE "/" "." target "${target}" )

  add_executable( ${target} "libraries/${path}" )
  target_link_libraries( ${target} PUBLIC stlab )
  add_test( NAME ${target} COMMAND ${target} )
endforeach()