include_directories(${PROJECT_SOURCE_DIR}/devLib)
include_directories(${PROJECT_SOURCE_DIR}/wiringPi)

set(WPI_GPIO_SRC gpio.c readall.c pins.c)

add_executable(gpio ${WPI_GPIO_SRC})
#set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/dist)

target_link_libraries(gpio libwiringPi libwiringPiDev -lpthread -lm)

install(TARGETS gpio RUNTIME DESTINATION bin)
