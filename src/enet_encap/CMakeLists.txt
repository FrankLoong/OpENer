#######################################
# Ethernet encapsulation library      #
#######################################

include_directories(
  ${INTTYPES_DIR}
  ${CMAKE_SOURCE_DIR}/src
  ${CMAKE_SOURCE_DIR}/src/cip
  ${CMAKE_SOURCE_DIR}/src/enet_encap
  ${CMAKE_SOURCE_DIR}/src/ports/${OpEner_platform}
  ${CMAKE_SOURCE_DIR}/src/ports/${OpEner_platform}/sample_application
  )

set( ENET_ENCAP_SRC
  cpf.h
  cpf.c
  encap.h
  encap.c
  endianconv.h
  endianconv.c
  )

add_library( ENET_ENCAP ${ENET_ENCAP_SRC} )
