add_subdirectory(sample_application)

include_directories(
  ${INTTYPES_DIR}
  ${CMAKE_SOURCE_DIR}
  ${CMAKE_SOURCE_DIR}/cip
  ${CMAKE_SOURCE_DIR}/enet/encap
  ${CMAKE_SOURCE_DIR}/ports
  )

set( source_files
  networkhandler.c
  main.c
  ./sampleapplication.c
  )

add_executable(OpENer ${source_files})

target_link_libraries(
  OpENer
  CIP
  ENET_ENCAP
  ${PLATFORM_SPEC_LIBS}
  )
