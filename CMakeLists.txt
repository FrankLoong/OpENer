#######################################
# Required CMake version              #
#######################################
cmake_minimum_required( VERSION 2.8.9 )

set( CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake )
set( CMAKE_USER_MAKE_RULES_OVERRIDE ${CMAKE_MODULE_PATH}/c_flag_overrides.cmake)

#######################################
# Project name                        #
#######################################
project( OpENer C )

#######################################
# Project version                     # 
#######################################
set( OpENer_VERSION_MAJOR 1 )
set( OpENer_VERSION_MINOR 2 )

find_path( INTTYPES_DIR inttypes.h ${PROJECT_SOURCE_DIR}/contrib/msinttypes)

if( WIN32 )
  set( OpEner_platform "WIN32" )
elseif( UNIX ) # UNIX or UNIX like (i.e. APPLE and CYGWIN)
  set( OpEner_platform "POSIX" )
else()
  set( OpEner_platform )
endif()

#######################################
# OpENer tracer switches              #
#######################################
set( OpENer_TRACES OFF CACHE BOOL "Activate OpENer traces" )
if(OpENer_TRACES)
  add_definitions( -DOPENER_WITH_TRACES )
  set( TRACE_LEVEL 0 )
  set( OpENer_TRACE_LEVEL_ERROR ON CACHE BOOL "Error trace level" )
  set( OpENer_TRACE_LEVEL_WARNING ON CACHE BOOL "Warning trace level" )
  set( OpENer_TRACE_LEVEL_STATE ON CACHE BOOL "State trace level" )
  set( OpENer_TRACE_LEVEL_INFO ON CACHE BOOL "Info trace level" )
  
  if(OpENer_TRACE_LEVEL_ERROR)
    math( EXPR TRACE_LEVEL "${TRACE_LEVEL} + 1" )
  endif(OpENer_TRACE_LEVEL_ERROR)
  if(OpENer_TRACE_LEVEL_WARNING)
    math( EXPR TRACE_LEVEL "${TRACE_LEVEL} + 2" )
  endif(OpENer_TRACE_LEVEL_WARNING)
  if(OpENer_TRACE_LEVEL_STATE)
    math( EXPR TRACE_LEVEL "${TRACE_LEVEL} + 4" )
  endif(OpENer_TRACE_LEVEL_STATE)
  if(OpENer_TRACE_LEVEL_INFO)
    math( EXPR TRACE_LEVEL "${TRACE_LEVEL} + 8" )
  endif(OpENer_TRACE_LEVEL_INFO)
  
  add_definitions(-DOPENER_TRACE_LEVEL=${TRACE_LEVEL})
  
endif(OpENer_TRACES)

#######################################
# Add subdirectories                  #
#######################################
add_subdirectory(src/cip)
#add_subdirectory(src/cip_objects)
add_subdirectory(src/enet_encap)
add_subdirectory(src/ports)
