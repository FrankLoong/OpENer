include_directories(
  ${INTTYPES_DIR}
  ${CMAKE_SOURCE_DIR}/src
  ${CMAKE_SOURCE_DIR}/src/cip
  ${CMAKE_SOURCE_DIR}/src/enet_encap
  ${CMAKE_SOURCE_DIR}/src/ports/${OpEner_platform}
  ${CMAKE_SOURCE_DIR}/src/ports/${OpEner_platform}/sample_application
  )


set( source_files
  networkhandler.h
  networkhandler.c
  main.c
  sample_application/sampleapplication.c
  )

add_executable(OpENer ${source_files})

target_link_libraries( OpENer
  CIP
  ENET_ENCAP
  ws2_32
  )
