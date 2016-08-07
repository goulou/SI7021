# Project name
project(Arduino_SI7021_${DEVICE_NAME})

# CMake version
cmake_minimum_required(VERSION 2.6)

message("Including ${PROJECT_NAME} for arch : ${ARDUINO_ARCH}")

file(GLOB SRC_FILES_CPP SI7021.cpp)
file(GLOB SRC_FILES_C )
file(GLOB FILE_HEADERS   ${CMAKE_CURRENT_SOURCE_DIR}/*.h ${CMAKE_CURRENT_SOURCE_DIR}/*.hpp)


add_library(${PROJECT_NAME} STATIC ${SRC_FILES_C} ${SRC_FILES_CPP} ${FILE_HEADERS})
set_target_properties(${PROJECT_NAME} PROPERTIES LINKER_LANGUAGE CXX)

target_include_directories(
	${PROJECT_NAME} PUBLIC
	${CMAKE_CURRENT_SOURCE_DIR}
	)
	
target_link_libraries(${PROJECT_NAME} Arduino_${DEVICE_NAME})
target_link_libraries(${PROJECT_NAME} Arduino_WIRE_${DEVICE_NAME})
