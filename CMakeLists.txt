cmake_minimum_required(VERSION 2.8)
project(wiringPi)

OPTION (WIRINGPI_BUILD_DEVLIB "Build WiringPi devLib" ON)
OPTION (WIRINGPI_BUILD_GPIO "Build WiringPi GPIO tool" ON)

IF (WIRINGPI_BUILD_DEVLIB)
  add_subdirectory(devLib)
ENDIF ()
IF (WIRINGPI_BUILD_GPIO)
  add_subdirectory(gpio)
ENDIF()
#add_subdirectory(pins)
add_subdirectory(wiringPi)

# Build deb package
# command to build *.deb
# cmake . && make && make package
SET(MAJOR_VERSION 2)
SET(MINOR_VERSION 32)
SET(PATCH_VERSION 0)
SET(CPACK_GENERATOR "DEB")
SET(CPACK_PACKAGE_VERSION_MAJOR "${MAJOR_VERSION}")
SET(CPACK_PACKAGE_VERSION_MINOR "${MINOR_VERSION}")
SET(CPACK_PACKAGE_VERSION_PATCH "${PATCH_VERSION}")
SET(CPACK_PACKAGE_DESCRIPTION "WiringPi Library for RaspberryPi")
INCLUDE(CPack)
