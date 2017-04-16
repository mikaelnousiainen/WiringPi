set(WPI_HEADERS
		wiringPi.h
		wiringSerial.h wiringShift.h
		wiringPiSPI.h wiringPiI2C.h
		softPwm.h softTone.h
		pseudoPins.h
		bmp180.h ds18b20.h htu21d.h
		mcp23008.h mcp23016.h mcp23017.h
		mcp23s08.h mcp23s17.h
		sr595.h	ads1115.h
		pcf8574.h pcf8591.h
		mcp3002.h mcp3004.h mcp4802.h mcp3422.h
		max31855.h max5322.h
		sn3218.h drcSerial.h
		rht03.h
		wpiExtensions.h)

set(WPI_SRC wiringPi.c
		wiringSerial.c wiringShift.c				
		piHiPri.c piThread.c					
		wiringPiSPI.c wiringPiI2C.c
		pseudoPins.c
		softPwm.c softTone.c ads1115.c
		bmp180.c ds18b20.c htu21d.c
		mcp23008.c mcp23016.c mcp23017.c			
		mcp23s08.c mcp23s17.c sr595.c												
		pcf8574.c pcf8591.c sn3218.c					
		mcp3002.c mcp3004.c mcp4802.c mcp3422.c
		max31855.c max5322.c drcSerial.c drcNet.c
		rht03.c
		wpiExtensions.c)

include_directories(${PROJECT_SOURCE_DIR}/wiringPi)

add_library(libwiringPi SHARED ${WPI_SRC})
target_link_libraries(libwiringPi pthread crypt rt)
set_target_properties(libwiringPi PROPERTIES OUTPUT_NAME "wiringPi")

#set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/dist)

install(FILES ${WPI_HEADERS} DESTINATION include)
install(TARGETS libwiringPi DESTINATION lib)
