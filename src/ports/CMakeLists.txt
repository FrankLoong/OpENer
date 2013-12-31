if( OpEner_platform )
  add_subdirectory( ${OpEner_platform} )
else()
  message( FATAL_ERROR "undefine platform" )
endif()

