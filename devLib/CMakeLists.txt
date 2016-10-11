set(WPI_DEVLIB_HEADERS
    ds1302.h gertboard.h lcd.h
    lcd128x64.h maxdetect.h piFace.h
    piGlow.h piNes.h scrollPhat.h scrollPhatFont.h)

set(WPI_DEVLIB_SRC ds1302.c maxdetect.c scrollPhat.c piNes.c gertboard.c piFace.c lcd128x64.c lcd.c piGlow.c)

include_directories(${PROJECT_SOURCE_DIR}/wiringPi)

add_library(libwiringPiDev SHARED ${WPI_DEVLIB_SRC})
add_definitions("-lpthread")

set_target_properties(libwiringPiDev PROPERTIES OUTPUT_NAME "wiringPiDev")

set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/dist)

install(FILES ${WPI_DEVLIB_HEADERS} DESTINATION include)
install(TARGETS libwiringPiDev DESTINATION lib)
