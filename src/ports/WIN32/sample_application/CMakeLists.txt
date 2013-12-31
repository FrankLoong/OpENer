#######################################
# Add common includes                 #
#######################################
include_directories(
  ${INTTYPES_DIR}
  ${CMAKE_SOURCE_DIR}
  ${CMAKE_SOURCE_DIR}/cip
  ${CMAKE_SOURCE_DIR}/enet/encap
  ${CMAKE_SOURCE_DIR}/ports
  )

#######################################
# Add platfrom specific things        #
#######################################

add_library(SAMPLE_APP
  sampleapplication.c
  )
