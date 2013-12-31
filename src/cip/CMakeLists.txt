#######################################
# CIP library                         #
#######################################

include_directories(
  ${INTTYPES_DIR}
  ${CMAKE_SOURCE_DIR}/src
  ${CMAKE_SOURCE_DIR}/src/cip
  ${CMAKE_SOURCE_DIR}/src/enet_encap
  ${CMAKE_SOURCE_DIR}/src/ports/${OpEner_platform}
  ${CMAKE_SOURCE_DIR}/src/ports/${OpEner_platform}/sample_application
  )

set( source_files
  appcontype.c
  appcontype.h
  cipassembly.c
  cipassembly.h
  cipclass3connection.c
  cipclass3connection.h
  cipcommon.c
  cipcommon.h
  cipconnectionmanager.c
  cipconnectionmanager.h
  ciperror.h
  cipethernetlink.c
  cipethernetlink.h
  cipidentity.c
  cipidentity.h
  cipioconnection.c
  cipioconnection.h
  cipmessagerouter.c
  cipmessagerouter.h
  ciptcpipinterface.c
  ciptcpipinterface.h
  ciptypes.h
  )

add_library( CIP ${source_files} )
